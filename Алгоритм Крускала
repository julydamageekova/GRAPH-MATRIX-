#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

    void KRSKL (vector <pair <int, pair <int, int> > >& G, int V, int E){
        int cost = 0;
        vector <pair <int,int> > res; // вектор с ребрами остовного дерева
        sort(G.begin(), G.end()); //сортировка вектора по весу ребра
        vector <int> tree_id (V); //номер дерева, котооому принадлежит вершина
        for (int i = 0; i < V; i++) //изначально каждая вершина лежит в своем дереве{
            tree_id[i] = i;
        for (int i = 0; i < E; i++){
            int a = G[i].second.first,  b = G[i].second.second,  l = G[i].first;
            if (tree_id[a] != tree_id[b]){ // если вершины не принадлежат одному поддереву
                cost += l; //добавить минимальное ребро
                res.push_back (make_pair (a, b)); // образовать между ними ребро
                int old_id = tree_id[b],  new_id = tree_id[a];
                for (int j=0; j < V; ++j) // переобозначить принадлежности поддереву
                    if (tree_id[j] == old_id)
                        tree_id[j] = new_id;
            }
        }

        for(int i = 0; i < res.size(); i++)
            cout << " "<< res[i].first << " " << res[i].second << endl;
    }

    void matrix(vector <pair <int, pair <int, int> > > & G, int E){
        cout << endl;
        for (int i = 0; i < E; i++){
            int temp;
            cout << " Enter edge: ";
            int k,l;
            cin >> k >> l;
            cout  << " Weight of "  << k << "-" << l << " : ";
            cin >> temp;
            cout << endl;
            G[i].first = temp;
            G[i].second.first = k;
            G[i].second.second = l;
        }

    }

    int main(){
        int V,E;
        cout << " Enter amount of vertices: ";
        cin >> V;
        cout << " Enter amount of edges: ";
        cin >> E;
        vector <pair <int, pair <int, int> > > G(E);
        matrix(G,E);
        cout << " Edges of new G: " << endl;
        KRSKL(G,V,E);
        return 0;
    }
