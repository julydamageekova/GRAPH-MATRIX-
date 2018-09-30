#include <iostream>
#include <stack>
using namespace std;

void topsort(int v, bool** G, bool* used, int V, stack <int>& main){
used[v] = 1;
for(int i = 0; i < V; i++){
    if((used[i] == 0)&&(G[v][i] == 1)){
        topsort(i, G, used, V, main);
        }
}
main.push(v);
}


void matrix (int V, int E, bool** G){
    for ( int i = 0; i < V; i++)
        for ( int j = 0; j < V; j++)
            G[i][j] = false;
    cout << " Enter edges :"<< endl;
    int k,l;
    for (int i = 0; i < E; i++){
        cout << " ";
        cin >> k >> l;
        G[k][l] = true;
    }
}

int main()
{
    int V, E;
    cout << " Enter amount of vertexes ";
    cin >> V;
    cout << " Enter amount of edges ( <= V!) ";
    cin >> E;
    bool** G = new bool* [V];
    for(int i = 0; i < V; i++)
        G[i]=new bool [V];
    matrix(V, E, G);
    bool used[V];
    for(int i = 0; i < V; i++)
        used[i] = 0;
    stack <int> main;
    for(int i = 0; i < V; i++)
        if(used[i] == 0)
            topsort(i, G, used, V, main);
    int ar[V];
    for (int i = 0; i < V; i++){
        ar[i] = main.top();
        main.pop();
        cout << ar[i] << "  ";
    }
    return 0;
}
