

### Linux 쉘 스크립트 작성

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



