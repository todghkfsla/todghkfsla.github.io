---
layout: single
title: "bin packing(통 채우기)"
date:   2020-03-27 11:07:30 +0900
categories: jekyll 
---

일단  다음적합코드를 하라했으니 다음 적합은 전에 물건을 넣은 통에 여유가 (만약에) 있다면 새 물건을 넣는 것인데 용량은 10이라고 하고 물건의 크기는 교수님이 보여준것처럼

[7,5,6,4,2,3,7,5]



![image](https://user-images.githubusercontent.com/62733873/83838253-9ef13500-a733-11ea-904b-bdd3628dbcaf.png)


그림으로 본다면 이런형태일것이다(그림은 알기쉬운 알고리즘 273쪽 그림)

처음에 7이 들어가고 그다음 5가들어가고 그다음 6 그다음 4 가 들어갔는데 무조건 다 채워젔다면 다음으로 넘어가야한다 그래서 2는 4번째통에 3도 4번째통 7은 안들어가니 다음통...

이렇게 작용하는 알고리즘이다.

그래서 밑에는 코드를 작성해 볼 것이다.

```c
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
int next(int le[],int k,int r)
{
    int bin=r;    //10
    int u=0;
    for(int i=0; i<k; i++){
       if(le[i]>bin){                   
           a++;
           bin=r-le[i];                 //3으로변했던게 ->5
       }
        else
            bin=bin-le[i];             //처음7->3
    }
    return u;
}
int main(void)
{
    int le[]={7,5,6,4,2,3,7,5};
     int k=sizeof(le)/sizeof(le[0]);   //8이 나오니 k=8
    int r=10;  //이건 통의 용량
    printf("요구 되는 다음 적합은 :%d",next(le,k,r)); //통이 필요한 수
    return 0;
}
```

실행결과는 이렇게 나온다 (교수님이 이런 결과를 원한건지는 몰라서 만약에 이 의도가 아니었다면 점수 안주셔도 됩니다.)

![image](https://user-images.githubusercontent.com/62733873/83838185-75d0a480-a733-11ea-8ee2-bbc1e192666f.png)


이러면  0번째 통에는 7만 들어가고

1번째 통에는 5만 들어가고

2번째 통에는 6이들가고 4가 위에 들가서 용량 풀

3번째 통에는 2랑 3이 들가고

4번째 통에는 7이 들가고

5번째 통에는 5가 들어간다.

