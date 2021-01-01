# Algorithm

방학동안 알고리즘 공부를 하면서 실력을 향상해보자!


## 코딩테스트 연습>해시>완주하지 못한 선수

### 문제 설명
&nbsp;수많은 마라톤 선수들이 마라톤에 참여하였습니다. 단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.<br>
마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요.

### 제한사항

* 마라톤 경기에 참여한 선수의 수는 1명 이상 100,000명 이하입니다. 
* completion의 길이는 participant의 길이보다 1 작습니다. 
* 참가자의 이름은 1개 이상 20개 이하의 알파벳 소문자로 이루어져 있습니다. 
* 참가자 중에는 동명이인이 있을 수 있습니다.

### 입출력 예
|participant|completion|return|
|------|---|---|
|[leo, kiki, eden]|[eden, kiki]|leo|
|[marina, josipa, nikola, vinko, filipa]|[josipa, filipa, marina, nikola]|vinko|
|[mislav, stanko, mislav, ana]|[stanko, ana, mislav]|mislav|

### 입출력 예 설명
예제 #1<br>
leo는 참여자 명단에는 있지만, 완주자 명단에는 없기 때문에 완주하지 못했습니다.

예제 #2<br>
vinko는 참여자 명단에는 있지만, 완주자 명단에는 없기 때문에 완주하지 못했습니다.

예제 #3<br>
mislav는 참여자 명단에는 두 명이 있지만, 완주자 명단에는 한 명밖에 없기 때문에 한명은 완주하지 못했습니다


### 나의 풀이
```python
def solution(participant, completion):
    participant_cnt = {}
    for i in participant:
        participant_cnt[i] = 0 

    for i in participant:
        if i in participant_cnt:
            participant_cnt[i] = participant_cnt[i]+1
    completion_cnt = {}
    for i in completion:
        completion_cnt[i] = 0 

    for i in completion:
        if i in completion_cnt:
            completion_cnt[i] = completion_cnt[i]+1


    for key in participant_cnt:
        try:
            if participant_cnt[key] != completion_cnt[key]:
                answer = key
        except:
            answer = key
    return answer
```  
### 우수코드
```python
import collections

def solution(participant, completion):
    answer = collections.Counter(participant) - collections.Counter(completion)
    return list(answer.keys())[0]
```

### 새로배운점
## collections.Counter를 이용한 카운팅
파이썬에서 제공하는 collections 모듈의 Counter 클래스를 사용하면 위 코드를 단 한 줄로 줄일 수가 있습니다.



