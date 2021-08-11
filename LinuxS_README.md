

#### Linux 쉘 스크립트 작성

------

(Step 1)  인터프리터 지시자 설정, 결과 파일 선언, 항목 선언

```
#!/bin/sh
RESULT_FILE="result.txt"
echo "[U-01] root 계정의 원격 접속 제한"
```



(Step 2) 점검파일 확인



(Step 3) 진단항목 결과 판단

```
if [ $TELNET -eq 1 -a $SSH -eq 1 ]
	then
		echo "[U-01] 양호" >> $RESULT_FILE 2>&1
	else
		echo "[U-01] 취약" >> $RESULT_FILE 2>&1
fi
unset TELNET
unset SSH
```

`unset TELNET`
`unset SSH` 		// TELNET, SSH 값 초기화

## 

(진단 항목 U-01) root 계정의 원격 접속 제한 보안 요구사항

```
[보안대책] 판단기준
∙양호 : 원격 터미널 서비스를 사용하지 않거나, 사용 시 root 직접 접속을 차단하는 경우
∙취약 : 원격 터미널 서비스를 사용 시 root 직접 접속을 허용한 경우
```

```
[보안대책] 조치방법
원격 접속 시 root 계정으로 직접 접속할 수 없도록 설정파일 수정
```



(진단 항목 U-07) /etc/passwd 파일 소유자 및 권한 설정 보안 요구사항

```
[보안대책] 판단기준
∙양호 : /etc/passwd 파일 소유자가 root이고, 권한이 644 이하인 경우
∙취약 : /etc/passwd 파일 소유자가 root가 아니거나 권한이 644 이하가 아닌 경우
```

```
[보안대책] 조치방법
/etc/passwd 파일 소유자 및 권한 변경 (소유자 root, 권한 644)
```

