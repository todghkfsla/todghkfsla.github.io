---
layout: single
title: "Approximating the value of Pi"
date: 2020-06-02 10:03:20 +0900
categories: jekyll
---

처음에는 원을 그린다음에 직관적으로 나오는 실행결과를 만들고 싶었지만 원을 만드는 방법을 c언어 시간이든 자바 시간이든 배우지 못해서 직관적으로 나타내지는 못하였다. 자세한 얘기는 아래 실행결과문을 보면서 더얘기할것이다.

```c
#include<stdlib.h>
#include<stdio.h>
#include<math.h>
#include<time.h>

void cirlce(int num);
int main(void)
{
    srand((double)time(NULL));
    int n;
    n=0;
    printf("동작 횟수(점의 개수)를 입력하세요 :");
    scanf("%d",&n);
    circle(n);
}
void circle(int num)
{
    double x,y;
    int i=0;
    int in=0;
    double di=0,pi=0;
    
    for(i=1; i<=num; i++){
        x=(double)rand()/(double)RAND_MAX;
        y=(double)rand()/(double)RAND_MAX;
        di=sqrt((x*x)+(y*y));
        if(di<=1){
            in++;
        }
    }
    pi=4.0*in/num;  //영상에 있는 거랑 똑같은 방법으로
    printf("원 내부의 점 개수 %d\n",in);
    printf("원 외부의 점 개수 :%d\n",num-in);
    printf("Pi의 값:%f",pi);
    return ;
}
```

아래쪽은 실행결과이다 첫번째로 점의 개수를 입력한다음에(여기서는 5000) 그러면 이제 

x랑 y값을 무작위로 받은뒤 if문에서 판단을 해서 원내부면 원내부의 점개수를 증가시키고 아니라면 원외부의 점개수를 증가할것이다 

그다음에 pi 값을 계산해주는 식이다. 

![image-20200601172518711](C:\Users\장석빈\AppData\Roaming\Typora\typora-user-images\image-20200601172518711.png)



코딩을 해보면서 아쉬운점은 유튜브 영상처럼 원을 그린다음에 원에서 내부의 점개수가 몇개면 그만큼 자그만한 원이 생기고하는 그런점을 못했다는 (실력부족으로)  점이 아쉬웠다.