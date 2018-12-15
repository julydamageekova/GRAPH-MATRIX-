#include <iostream>
#include <vector>
using namespace std;

IS_CUTPOINT(int v){
cout << endl << "  V = " << v << endl << endl;
}
void dfs (bool* used, int v, int p, int* tin,int* fup,int timer, vector<vector<int> >& G) {
	used[v] = true;
	tin[v] = fup[v] = timer++;
	int children = 0;
	for (size_t i=0; i<G[v].size(); ++i) {
		int to = G[v][i];
		if (to == p)  continue;
		if (used[to])
			fup[v] = min (fup[v], tin[to]);
		else {
			dfs (used, to, v,tin, fup,timer,G);
			fup[v] = min (fup[v], fup[to]);
			if (fup[to] >= tin[v] && p != -1)
				IS_CUTPOINT(v);
			++children;
		}
	}
	if (p == -1 && children > 1)
		IS_CUTPOINT(v);
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
	dfs (used,0,-1,tin,fup, timer, G);
    return 0;
}
