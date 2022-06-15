## SCP 성공/실패 파일 작성하는 방법
- `scp sourcefile.txt user@targetsystem:/home/test/dir1 && echo "scp 완료" || echo "실패" > out.txt`
