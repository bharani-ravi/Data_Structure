#include<stdio.h>
#include<stdlib.h>
int source,v,e,time,visited[20],G[20][20];
void DFS(int i)
{
    int j;
    visited[i]=1;
    printf("%d->",i+1);
    for(j=0;j<v;j++)
    {
        if(G[i][i]==1&&visited[j]==0)
        {
            DFS(j);
        }
    }
}
int main()
{
    int i,j,v1,v2;
    printf("Graphs\n");
    printf("Enter no. of edges:");
    scanf("%d",&e);
    printf("Enter no. of vertices:");
    scanf("%d",&v);
    for(i=0;i<v;i++)
    {
        for(j=0;j<v;j++)
        {
         G[i][j]=0;   
        }
    }
    for(i=0;i<e;i++)
    {
        printf("Enter the edges (format:V1 V2):");
        scanf("%d%d",&v1,&v2);
        G[v1-1][v2-1]=1;
    }
    for(i=0;i<v;i++)
    {
        for(j=0;j<v;j++)
        {
            printf("%d",G[i][j]);
        }
        printf("\n");
    }
    printf("Enter the source:");
    scanf("%d",&source);
    DFS(source -1);
    return 0;
}

Output:
Graphs
Enter no. of edges:6
Enter no. of vertices:4
Enter the edges (format:V1 V2):1 1
Enter the edges (format:V1 V2):1 2
Enter the edges (format:V1 V2):1 3
Enter the edges (format:V1 V2):1 4
Enter the edges (format:V1 V2):2 4
Enter the edges (format:V1 V2):3 4
1111
0001
0001
0000
Enter the source:1
1->2->3->4->
