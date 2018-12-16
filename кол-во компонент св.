#include <iostream>

using namespace std;

void dfs(int v, bool** G, bool* used, int V){
used[v] = 1;
for(int i = 0; i < V; i++){
    if((used[i] == 0)&&(G[v][i] == 1)){
        dfs(i, G, used,V);
    }
}

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
        G[l][k] = true;
    }
     for ( int i = 0; i < V; i++){
        for ( int j = 0; j < V; j++){
            cout << G[i][j]<< " ";
        }
        cout << endl;
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
    int k = 0;
    bool used[V];
    for(int i = 0; i < V; i++)
        if(used[i] == 0){
            k++;
            dfs(i, G, used, V);
        }
    cout << " Components = " << k << endl;
    return 0;
}
