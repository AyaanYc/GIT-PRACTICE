vi입력모드
작업 Vi 명령어 상세
입력 시작 i 명령어 입력 모드에서 텍스트 입력 모드로 전환
입력 종료 ESC 텍스트 입력 모드에서 명령어 입력 모드로 전환
저장 없이 종료 :q
저장 없이 강제 종료 :q! 입력한 것이 있을 때 사용
저장하고 종료 :wq 입력한 것이 있을 때 사용
위로 스크롤 k git log등에서 내역이 길 때 사용
아래로 스크롤 j git log등에서 내역이 길 때 사용

reset 사용해서 과거로 돌아가기
git log
되돌아갈 시점: Add team Cheetas의 커밋 해시 복사
git reset --hard (돌아갈 커밋 해시)

revert
git revert (되돌릴 커밋 해시)

커밋해버리지 않고 revert하기
git revert --no-commit (되돌릴 커밋 해시)
원하는 다른 작업을 추가한 다음 함께 커밋
취소하려면 git reset --hard

revert로 커밋 되돌리는데 커밋사이에 겹치는 파일 수정이 있으면 오류가 터진다
그럴땐 오류내용을 찾아서
git rm leopards.yaml로 Git에서 해당 파일 삭제
git revert --continue로 마무리
:wq로 커밋 메시지 저장
이런식으로해결

add-coach란 이름의 브랜치 생성
git branch add-coach

브랜치 목록 확인
git branch

add-coach 브랜치로 이동
git switch add-coach

브랜치 생성과 동시에 이동하기
git switch -c new-teams

브랜치 삭제하기
git branch -d (삭제할 브랜치명)
-D는 강제삭제(다른브랜치에 commit이 적용이 안되있을경우)
지워질 브랜치에만 있는 내용의 커밋이 있을 경우
즉 다른 브랜치로 가져오지 않은 내용이 있는 브랜치를 지울 때

브랜치 이름 바꾸기
git branch -m (기존 브랜치명) (새 브랜치명)

여러 브랜치의 내역 편리하게 보기
git log --all --decorate --oneline --graph

브랜치 합치는 방식
merge : 두 브랜치를 한 커밋에 이어붙입니다.
브랜치 사용내역을 남길 필요가 있을 때 적합한 방식입니다.
다른 형태의 merge에 대해서도 이후 다루게 될 것입니다.

    rebase : 브랜치를 다른 브랜치에 이어붙입니다.
        한 줄로 깔끔히 정리된 내역을 유지하기 원할 때 적합합니다.
        이미 팀원과 공유된 커밋들에 대해서는 사용하지 않는 것이 좋습니다.

브랜치 충돌오류
merge
당장 충돌 해결이 어려울 경우 아래 명령어로 merge 중단
git merge --abort

    해결 가능 시 충돌 부분을 수정한 뒤 git add ., git commit으로 병합 완료

rebase
당장 충돌 해결이 어려울 경우 아래 명령어로 merge 중단
git rebase --abort

    해결 가능 시 충돌 부분을 수정한 뒤 git add . 아래 명령어로 계속
    git rebase --continue(커밋이된다)
    충돌이 모두 해결될 때까지 반복
