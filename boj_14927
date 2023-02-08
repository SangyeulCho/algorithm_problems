#include <cstdio>

int a[22][22];
int b[2][22];
int d[22][22];

int main(){
	int n, ret = 999;
	bool state = true;
	scanf("%d", &n);
	for(int i=1;i<=n;i++){
		for(int j=1;j<=n;j++){
			scanf("%d", &a[i][j]);
			if(a[i][j]!=0) state = false;
		}
	}
	if(state) {
		printf("0\n");
		return 0;
	}
	for(int bit=0;bit<(1<<n);bit++){
		int cnt=0;
		for(int j=1;j<=n;j++){
			b[1][j] = (bit&(1<<(j-1)))?1:0;
			d[1][j] = b[1][j] ^ b[1][j-1] ^ ((bit&(1<<j))?1:0) ^ a[1][j];
			cnt+=b[1][j];
		}
		
		for(int i=2;i<=n;i++){
			for(int j=1;j<=n;j++){
				b[i%2][j] = d[i-1][j];
				d[i][j] = d[i-1][j] ^ d[i-1][j-1] ^ d[i-1][j+1] ^ b[(i+1)%2][j] ^ a[i][j];
				cnt += b[i%2][j];
			}
		}

		state = true;
		for(int j=1;j<=n;j++){
			if(d[n][j]!=0){
				state = false;
			}
		}
		if(state && cnt<ret) ret = cnt;
	}
	printf("%d\n", ret!=999?ret:-1);
	return 0;
}
