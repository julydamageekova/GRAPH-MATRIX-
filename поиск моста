#include <iostream>
#include <vector>
using namespace std;

void IS_BRIDGE(int v, int to){
cout << endl << endl << " : " << v <<" - " << to << endl << endl;
}
void dfs (bool* used, int v, int p, int* tin,int* fup,int timer, vector<vector<int> >& G) {
	used[v] = true;
	tin[v] = fup[v] = timer++;
	for (size_t i=0; i<G[v].size(); ++i) {
		int to = G[v][i];
		if (to == p)  continue;
		if (used[to])
			fup[v] = min (fup[v], tin[to]);
		else {
			dfs (used,to,v,tin,fup, timer, G);
			fup[v] = min (fup[v], fup[to]);
			if (fup[to] > tin[v])
				IS_BRIDGE(v,to);
		}
	}
}

void find_bridges(bool* used, int n, int* tin,int* fup,int timer, vector<vector<int> >& G) {
	timer = 0;
	for (int i=0; i<n; ++i)
		used[i] = false;
	for (int i=0; i<n; ++i)
		if (!used[i])
			dfs (used,i,-1,tin,fup, timer, G);
}

int main(){
    int n,m,v,u;
    cout <<" Number of vertices "; cin >> n;
    cout <<" Number of edges "; cin >> m;
    cout <<" Incidence edges" << endl;
    vector <vector<int> > G(n);
    for (int i = 0; i < m; i++){
        cin >> v >> u;
       G[v].push_back(u);
       G[u].push_back(v);
    }
   for(int i = 0;i < G.size();i++){
   cout << i << " : ";
    for(int j = 0; j < G[i].size(); j++)
        cout << G[i][j] << ",";
    cout<<endl;

   }

   int timer = 0;
   bool used[n];
   int tin[n], fup[n];
	for (int i=0; i<n; ++i)
		used[i] = false;
	find_bridges(used,n,tin,fup, timer, G);
    return 0;
}
