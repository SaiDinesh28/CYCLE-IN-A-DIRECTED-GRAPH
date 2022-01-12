# CYCLE-IN-A-DIRECTED-GRAPH
#include<bits/stdc++.h>
using namespace std;
bool checkcycle(vector<int>adj[],int node,int vis[],int dfsvis[]){
    vis[node]=1;
    dfsvis[node]=1;
    for(auto it:adj[node]){
        if(vis[it]==0){
            vis[it]=1;
            if(checkcycle(adj,it,vis,dfsvis)) return true;
        }
        else if(dfsvis[it]==1) return true;
        dfsvis[it]=0;
    }
    return false;
}
bool checkcycle(vector<int>adj[],int n){
    int vis[n],dfsvis[n];
    memset(vis,0,sizeof(vis));
    memset(dfsvis,0,sizeof(dfsvis));
    for(int i=0;i<n;i++){
        if(vis[i]==0){
            if(checkcycle(adj,i,vis,dfsvis)) return true;
        }
    }
    
    return false;
}
int main(){
    int t;
    cin>>t;
    while(t--){
        int n,m;
        cin>>n>>m;
        vector<int>adj[n];
        for(int i=0;i<m;i++){
            int u,v;
            cin>>u>>v;
            adj[u].push_back(v);
          //  adj[v].push_back(u);
        }
        if(checkcycle(adj,n)) cout<<"yes"<<endl;
        else cout<<"No"<<endl;
    }
}
