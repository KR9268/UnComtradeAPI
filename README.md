# UnComtradeAPI

## 개요
* UN Comtrade 에서 직접 받기 어려워서 API사용하기 위한 샘플코드
  * UN Comtrade : https://comtradeplus.un.org/TradeFlow
  * UN Comtrade Developer : https://comtradedeveloper.un.org/

# 필수사항
* comtradeapicall 파이썬 패키지 설치
```python
    pip install comtradeapicall
```
* API Subscription Key 발급 : UN Comtrade Developer에서 발급
  (https://comtradedeveloper.un.org/)
  * 가입 후 사용하고자 하는 API를 Subscription 
  * Profile 메뉴에서 Subscription내역이 보이고, Show로 Key를 확인할 수 있음

## 사용법
* 첫번째 칸에서 필수정보 입력 후 실행
```python
    subscription_key = 'your api key'
    directory = 'your download directory'
```
* 두번째 칸에서 조회정보 입력 후 실행
```python
    hscode = '288512,281325'
    flow_code = 'M,X' # M : Import / X : Export
```
* 원하는 기능으로 이동하여 진행
  * 저장없이 데이터 일부 확인 → `Subscription key 필요없는 일부 데이터 확인용 코드`로 이동
    * 조회조건(월)입력 후 바로 아래 칸 실행
  * **특정 연도** 데이터 저장 필요 → `Subscription key 필요한 다운로드 코드`로 이동
    * `조회조건 입력 (연단위)`에서 `4자리 연도` 입력하거나, `조회조건 입력 (월단위)`에서 `6자리 연월` 입력
    * 입력 후 `CSV파일 저장(1개월씩 저장)` 부분 실행
  * **특정 월** 데이터 저장 필요 → `### Subscription key 필요한 다운로드 코드 (반복문없이 1건 실행)`로 이동
    * `# 조회조건 입력 (월단위)`에서 `6자리 연월` 입력
    * 입력 후 `CSV파일 저장(1개월씩 저장)` 부분 실행

* 받아진 데이터의 Row 확인 (한번에 너무 많은 행 받으면 Block당하므로 점검용)
  * 실행하면 저장된 파일들에 대해 정보 제공
  ```python
    The file 282540,283324_202404.csv has 136 rows.
    The total : 970.
  ```

* 데이터 프레임 합치기
  * 실행하면 저장되어있는 파일을 하나로 합친다