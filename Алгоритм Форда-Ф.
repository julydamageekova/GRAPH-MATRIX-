#include <stdio.h>
#include <iostream>
#include <fstream>

using namespace std;

int V;            // число вершин в графе
const int INF = 10000; // условное число, обозначающее бесконечность

int** f; // f[i][j] - поток, текущий от вершины i к j
int** G;  // c[i][j] - максимальная величина потока, способная течь по ребру (i,j)

									// набор вспомогательных переменных, используемых функцией FindPath - обхода в ширину
int* Flow;    // Flow - значение потока через данную вершину на данном шаге поиска
int* Link;  // Link[i] хранит номер предыдущей вешины на пути i -> исток
int* Queue; // очередь
int QP, QC;              // QP - указатель начала очереди и QC - число эл-тов в очереди

// поиск пути, по которому возможно пустить поток алгоритмом обхода графа в ширину
// функция ищет путь из истока в сток, по которому еще можно пустить поток,
// считая вместимость ребера (i,j) равной G[i][j] - f[i][j]

int FindPath(int source, int target) // source - исток, target - сток
{
	QP = 0; QC = 1; Queue[0] = source;
	Link[target] = -1;
	int CurVertex;
	for (int i = 0; i < V; ++i)
		Flow[i] = 0;
	Flow[source] = INF;
	while (Link[target] == -1 && QP < QC)
	{
		CurVertex = Queue[QP];
		for (int i = 0; i < V; i++)
			if ((G[CurVertex][i] - f[CurVertex][i]) > 0 && Flow[i] == 0)
			{
				Queue[QC] = i;
				QC++;
				Link[i] = CurVertex;
				if (G[CurVertex][i] - f[CurVertex][i] < Flow[CurVertex])
					Flow[i] = G[CurVertex][i];
				else
					Flow[i] = Flow[CurVertex];
			}
		QP++;

	}

	if (Link[target] == -1) return 0;
	CurVertex = target;
	while (CurVertex != source)
	{
		f[Link[CurVertex]][CurVertex] += Flow[target];
		CurVertex = Link[CurVertex];
	}
	return Flow[target];
}

// основная функция поиска максимального потока
int MaxFlow(int source, int target) // source - исток, target - сток
{
	for (int i = 0; i < V; ++i){
		for (int j = 0; j < V; ++j){
			f[i][j] = 0;
		}
	}
	int MaxFlow = 0;
	int AddFlow;
	do{
		AddFlow = FindPath(source, target);
		MaxFlow += AddFlow;
	} while (AddFlow > 0);
	return MaxFlow;
}

void matrix(int V){
	for (int i = 0; i < V; ++i)
		for (int j = 0; j < V; ++j)
			G[i][j]=0;

			int numb, i,j;
			cout << endl << "Enter the elements in the following order:'i'->'j'->'numb'(G[i][j]=numb)." << endl << "When will you finish, enter '0->0->0'." << endl;
			cin >> i >> j;
			cout << "G[" << i << "][" << j << "]=";
            cin >> numb;

			while(numb!=0){
              G[i][j]=numb;
                cin >> i >> j;
                cout << "G[" << i << "][" << j << "]=";
                cin >> numb;
			}

}

int main(){
    int source, target;
    cout << "Enter V - ";
    cin >> V;

    cout << "source - ";
    cin >> source;
    cout << "target - ";
    cin >> target;

	f = new int*[V];
	G = new int*[V];
	for (int i = 0; i < V; ++i)
	{
		f[i] = new int[V];
		G[i] = new int[V];
	}

	matrix(V);
	Flow = new int[V];
	Link = new int[V];
	Queue = new int[V];

	int maxflow = MaxFlow(source, target);

	cout << "MaxFlow = " << maxflow <<  endl;

	delete[] f;
	delete[] G;
	delete[] Flow;
	delete[] Link;
	delete[] Queue;
	return 0;
}
