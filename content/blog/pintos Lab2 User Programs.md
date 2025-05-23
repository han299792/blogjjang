
가장 먼저, argument passing을 구현해야 하ㄴ다고 나와있다.이를 위해, 프로세스를 실행시킬 때file_name을 문자열로 받아와 작업 해야 한다. 

## strtok_r()의 핵심, save_ptr
file_name을 복사해와서, 명령어와 인자로 쪼개려고 한다. 이때 복사할 때 `strtok_r()` 를 사용하다. 
```c
strtok_r(char *str, const char *delim, char **save_ptr)
```

복사하는 비슷한 기능을 가진 함수에는 strtok() 가 있다. 하지만 helpful 한 pintos는 친절하게 
```c
#define strtok dont_use_strtok_use_strtok_r
```

이렇게 적어둔다. 

이에 대한 이유는
첫째, 원본 데이터의 무결성을 보장하지 않고
두번째, thread_safty 하지 않기 때문이다. 
https://hackerpark.tistory.com/entry/C%EC%96%B8%EC%96%B4-strtok-%ED%95%A8%EC%88%98-%EB%AC%B8%EC%9E%90%EC%97%B4-%EC%9E%90%EB%A5%B4%EA%B8%B0
이 사이트에 더 자세한 내용이 나와있다. 