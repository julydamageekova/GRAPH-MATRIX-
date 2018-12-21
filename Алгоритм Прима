#include <iostream>
#include <vector>
using namespace std;

    int PRM(int**G,int V){
        const int INF = 1000000000;
        bool used[V];//массив непосещенных вершин
        for(int i = 0; i < V; i++)
            used[i] = false;
        vector <int> min_e (V, INF), sel_e (V, -1);
        min_e[0] = 0;
        for (int i = 0; i < V; ++i) {
            int v = -1;
            for (int j = 0; j < V; ++j)
                if (!used[j] && (v == -1 || min_e[j] < min_e[v]))
                    v = j;//ищем непосещенное ребро с минимальным ребром 
            if (min_e[v] == INF) {
                cout << "No MST!";
                return 0;
            }
            used[v] = true;
            if (sel_e[v] != -1)
                cout <<" "<< v << "-" << sel_e[v] << endl;
            for (int to = 0; to < V; ++to)
                if (G[v][to] < min_e[to]) {
                    min_e[to] = G[v][to];
                    sel_e[to] = v;
                }
        }
        return 0;
    }

    void matrix(int**G, int V){
        int E;

        for (int i = 0; i<V; i++)
            for (int j = 0; j<V; j++)
                G[i][j] = 1000000;
        cout << " Enter amount of edges: ";
        cin >> E;
        cout << endl;
        for (int i = 0; i<E; i++){
            int temp;
            cout << " Enter edge: ";
            int k,l;
            cin >> k >> l;
            cout  << " Weight of "  << k << "-" << l << " : ";
            cin >> temp;
            cout << endl;
            G[k][l] = temp;
            G[l][k] = temp;
        }
    }

    int main(){
        int V;
        cout << " Enter amount of vertices: ";
        cin >> V;
        int **G = new int*[V];
            for(int i = 0; i < V; i++)
            G[i] = new int [V];
        matrix(G,V);
        cout << " Edges of new G: " << endl;
        PRM(G,V);
        return 0;
    }
