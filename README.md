#include <stdio.h>
int ans;
vis[10][10],map[10][10]={
1 , 1, 1, 1 ,1 ,1, 1, 1, 1, 1,
1 ,0, 0 ,1, 0, 0, 0 ,1 ,0 ,1,
1 ,0, 0 ,1 ,0 ,0, 0, 1 ,0, 1,
1 ,0 ,0 ,0 ,0, 1, 1 ,0, 0, 1,
1, 0 ,1 ,1 ,1 ,0 ,0 ,0 ,0 ,1,
1 ,0 ,0 ,0 ,1 ,0 ,0 ,0 ,0 ,1,
1 ,0 ,1 ,0 ,0 ,0 ,1 ,0 ,0 ,1,
1 ,0 ,1 ,1 ,1 ,0 ,1 ,1 ,0 ,1,
1 ,1 ,0 ,0 ,0 ,0 ,0 ,0 ,0 ,1,
1 ,1 ,1, 1 ,1 ,1 ,1 ,1 ,1 ,1
};
void dfs(int i,int j,int cnt,int ex,int ey)
{
    if(i<0||i>9||j<0||j>9||vis[i][j]||map[i][j]||cnt>=ans)return;
    if(i==ex&&j==ey)
    {
        ans=cnt;
        return;
    }

    vis[i][j]=1;       // 这个已经遍历了x`

    dfs(i,j-1,cnt+1,ex,ey);
    dfs(i-1,j,cnt+1,ex,ey);
    dfs(i,j+1,cnt+1,ex,ey);
    dfs(i+1,j,cnt+1,ex,ey);

    vis[i][j]=0;
}

int main()
{
		int m;
        scanf_s("%d",&m);
		int sx=1,sy=1,ex=m-2,ey=m-2;
        ans=100;
        dfs(sx,sy,0,ex,ey);
        if(ans=100) printf("No solution"); 
		else      printf("%d\n",ans);
    return 0;
}
