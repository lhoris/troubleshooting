# SFTP 업로드 실패시

#### logging level을 상향해서 실행
```bash
$ sftp -v vagrant@192.168.1.101
```

#### [핵심 에러 메시지]
```
Received message too long 1248161387
Ensure the remote shell produces no output for non-interactive sessions.
```

#### [원인]
`.bashrc, .profile, .bash_profile 등에서 echo, print 문이 있는 경우`

#### [해결방법]
해당 파일들에서 조건문을 추가하여 interactive session에서만 echo, print 문을 포함한 스크립트 수행

```
if [[ $- == *i* ]]; then
    # interactive shell일 때만 실행할 명령어들
    echo "Welcome vagrant"
fi
```