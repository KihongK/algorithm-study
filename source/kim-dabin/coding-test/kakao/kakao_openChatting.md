# [카카오/자바] 오픈채팅방

https://programmers.co.kr/learn/courses/30/lessons/42888



## 접근 방식

- 채팅방에 있는 유저들의 아이디(Key)와 닉네임(Value)을 hashMap에 저장 
- 닉네임 변경을 제외한 유저들의 행동 로그를 Queue에 저장 



1. 들어오거나 닉네임을 바꿀 때, hashMap에 저장
2. hashMap에 Change를 제외한, 행동로그에 따른 메세지를 저장  
   1. key "Enter" - value "들어왔습니다." 
   2. key "Leave" - value "나갔습니다."
3. "Change"를 제외한, 행동 로그를 UserLog 객체 타입으로 Queue로 저장 
   1. UserLog(id, action)
4. 1~3까지의 기록 처리가 끝나면, Queue에 저장된 로그를 문자열 배열 형태로 return



## 소스 구현

```java
import java.util.HashMap;
import java.util.LinkedList;
import java.util.Queue;

class Solution {
	
	public class UserLog{
		String id;
		String action;
		public UserLog(String id, String action) {
			this.id = id;
			this.action = action;
		}
	}
	
    public String[] solution(String[] record) {
	        String[] answer = null;
	        StringBuffer log = new StringBuffer();
	        Queue<UserLog> userLogQue = new LinkedList<>();
	        HashMap<String, String> map = new HashMap<String, String>();
	        
	        map.put("Enter","들어왔습니다.");
	        map.put("Leave","나갔습니다.");
	        
	        for(String r : record) {
	        	String[] user = r.split(" ");
	        	
	        	if(user.length==3) {
	        		
	        		map.put(user[1], user[2]);
	        	}
	        	if(!(user[0].equals("Change"))){
	        		userLogQue.add(new UserLog(user[1], user[0]));
	        	}
	        }
	        answer = new String[userLogQue.size()];
	        int i =0; 
	        while(!userLogQue.isEmpty()) {
	        	log.setLength(0);
	        	UserLog ul = userLogQue.poll();
	        	log.append(map.get(ul.id));
	        	log.append("님이 ");
	        	log.append(map.get(ul.action));
	        	answer[i++] = log.toString();
	        }   
	        return answer;
	    }
}
```



## 효율성 테스트

```tex
테스트 1 〉	통과 (2.61ms, 50.2MB)
테스트 2 〉	통과 (2.22ms, 52.2MB)
테스트 3 〉	통과 (2.48ms, 51.9MB)
테스트 4 〉	통과 (2.92ms, 52.8MB)
테스트 5 〉	통과 (11.42ms, 53.5MB)
테스트 6 〉	통과 (11.40ms, 53.1MB)
테스트 7 〉	통과 (11.49ms, 53.3MB)
테스트 8 〉	통과 (11.79ms, 53.2MB)
테스트 9 〉	통과 (10.79ms, 54.8MB)
테스트 10 〉	통과 (10.43ms, 55MB)
테스트 11 〉	통과 (7.23ms, 53.1MB)
테스트 12 〉	통과 (6.27ms, 53MB)
테스트 13 〉	통과 (10.42ms, 55.3MB)
테스트 14 〉	통과 (15.91ms, 53.3MB)
테스트 15 〉	통과 (2.26ms, 52.4MB)
테스트 16 〉	통과 (2.59ms, 51.9MB)
테스트 17 〉	통과 (3.27ms, 52.3MB)
테스트 18 〉	통과 (3.38ms, 52.9MB)
테스트 19 〉	통과 (14.52ms, 55.4MB)
테스트 20 〉	통과 (9.79ms, 52.6MB)
테스트 21 〉	통과 (8.27ms, 55MB)
테스트 22 〉	통과 (8.95ms, 53.6MB)
테스트 23 〉	통과 (14.17ms, 54.8MB)
테스트 24 〉	통과 (18.02ms, 55MB)
테스트 25 〉	통과 (214.38ms, 157MB)
테스트 26 〉	통과 (279.81ms, 158MB)
테스트 27 〉	통과 (335.39ms, 167MB)
테스트 28 〉	통과 (297.52ms, 164MB)
테스트 29 〉	통과 (227.35ms, 164MB)
테스트 30 〉	통과 (248.47ms, 158MB)
테스트 31 〉	통과 (212.65ms, 150MB)
테스트 32 〉	통과 (213.35ms, 146MB)
```

