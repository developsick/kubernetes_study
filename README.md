# Kubernetes 기본 개념 및 관련 .yaml

## 1. kubectl 설치
 * Install kubectl binary using curl 검색후
 * curl 뒤의 주소로 다운
 * https://storage.googleapis.com/kubernetes-release/release/v1.12.0/bin/windows/amd64/kubectl.exe
 * exe 파일을 적당히 넣고 해당폴더 주소를 path에 등록
 * kubectl --help 커맨드 먹히면 정상

## 2. CLOUDZ(ZCP) 연결 : master-work 노드 세팅
 * https://labs-console.cloudzcp.io 접속
 * id / pw : edu4@sk.com / edu1234!

## 3. 클러스터의 credential 정보 복사
 * 계정 > CLI Command의 내용을 전부 복사
 * (windows기준)사용자폴더에 .kube디렉토리 생성후 config라는 파일 생성-내용 복사
 * kubectl config get-contexts 라면 해당 정보가 조회가 되어야함
 * macOS의 경우는 cd $HOME/.kube 에 있는 config 파일을 vi로 열어 CLI Command 내용을 복사

## 4. deployment.yaml로 deployment 생성
 * deployment.yaml파일 .kube/workspace에 생성
 * kubectl apply -f deployment.yaml -n edu4 실행
  - deployment.apps/nginx-deployment created라고 뜨면 성공
 * kubectl get deploy -n edu4 : namespace edu4의 deploy정보 조회
 * kubectl get pods -n edu4 : namespace edu4에 속한 pod정보 조회

## PVC 생성시에는 apply 대신 create 명령어 사용
 * apply는 merge 개념으로 동일한 내용이 있으면 업데이트
 * storage는 변경에 critical하기 때문에 create를 사용하면 동일한 내용의 경우 업데이트 하지 않고 에러
