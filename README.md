Question:https://codeforces.com/problemset/problem/1872/G
                
                import sys
                inf=int(1e9)
                
                def read(T=int):
                	return [T(i) for i in sys.stdin.readline().split()]
                
                def solve():
                	n,a=read()[0],read()
                	ii,prd=[],1
                	for i in range(n):
                		prd=min(inf,prd*a[i])
                		if a[i]-1:
                			ii.append(i)
                	if prd==inf:
                		print(ii[0]+1,ii[-1]+1)
                		return
                	k,L,R,ans=len(ii),0,0,0
                	for i in range(k):
                		for j in range(i+1,k):
                			old,new=0,1
                			for x in range(i,j+1):
                				new=(new*a[ii[x]])
                				old+=a[ii[x]]
                			cur=new-old-((ii[j]-ii[i]+1)-(j-i+1))
                			if cur>ans:
                				ans,L,R=cur,ii[i],ii[j]
                	print(L+1,R+1)
                
                def main():
                	for i in range(read(int)[0]):
                		solve()
                
                main()
