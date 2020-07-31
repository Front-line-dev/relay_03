## :two_men_holding_hands: ​부캠나우(나우누리) (20200731 - v1.0.0)

### :pushpin: 나우누리 소개

- 추억의 **나우누리**를 기리는 커뮤니티 서비스.

  

### :closed_book: 만들 서비스 소개

- 기존의 클린 했던 나우누리의 상황을 재현 하기 위한 **A: 욕설 필터링 기능**과 현재 존재하는 다른 커뮤니티와의 차이를 만들기 위해서 **B: 둘 중 하나, C: 유저 추천** 기능을 추가하였다.

- 여기서 **둘 중 하나** 기능은 유저의 유치를 위한 재미 요소로 추가하였다.

  

### :man: 서비스 대상

- 부스트 캠퍼와 스태프, 마스터님



### :book: 일반 서비스 제공 요구사항 명세

| 구분  | 요구사항                                                     | 산출물                                                     |
| ----- | ------------------------------------------------------------ | ---------------------------------------------------------- |
| 2주차 | - 댓글 기능이 구현된 게시판(코딩, 아재개그, 운동, 음악, 역사, 맛집, 음주 등)<br />- 임시데이터 수집을 위해 구글폼으로 slack에 올린 후에 .csv파일로 Repository에 업로드<br />- 임시 데이터는 4주차에 사용될 활동이나 MBTI기반으로 그룹으로 유저를 추천해주기 위해 필요하다.<br />- 따라서 회원(이름, MBTI 정보, 관심사)가 필요할 것으로 보인다.<br />- 관심사(코딩, 운동, 음악, 역사, 맛집탐방, 음주 등) | 게시판 페이지<br />회원MBTI.csv                            |
| 3주차 | 회원가입 - 받을 데이터(아이디, 패스워드, 닉네임, MBTI, 관심사)<br />로그인 - JWT 방식<br />프로필수정 | 회원가입 페이지<br />로그인 페이지<br />프로필 수정 페이지 |
| 4주차 | 메인화면 구현(전체적인 디자인 수정), 게시글의 좋아요(하트) 기능 | 메인화면 페이지                                            |



### :book: 인공지능 서비스 제공 기능 명세

| 구분   | 기능명      | 설명                                                         | 주/서브 |
| ------ | ----------- | ------------------------------------------------------------ | ------- |
| 기능 A | 욕설 필터링 | **욕설, 비방을 걸러주는 기능** [[참조](https://github.com/hjh010501/appropriate-filetering)]<br />게시판과 댓글에 올라오는 스팸이나 욕설/비방을 필터링 해주는 것입니다.<br />욕설에 해당하는 문자는 *로 표기합니다. | 주      |
| 기능 A | 읽음이      | **CSS 서비스를 통해 시각장애인을 위한 글 읽어주는 서비스** [[참조](https://www.ncloud.com/product/aiService/css)]<br />예전에는 시각 장애인이 나우누리 서비스를 쓰지 못했는데 음성지원을 통한<br />서비스를 이용할 수 있도록 한다. | 서브    |
| 기능 B | 둘 중 하나  | **teachable machine을 통한 1:1 비교** [[참조](https://teachablemachine.withgoogle.com/train)]<br /><br />자신의 이미지나 웹캠을 통한 얼굴을 업로드하고 그에 대한 결과값을 출력해주는 것입니다.<br />teachable machine을 통해 여러 장의 이미지를 학습합니다.<br />예제) 사자와 토끼를 학습시키고 사용자가 얼굴을 등록하면 웹 페이지에 "당신은 사자와 더 닮았습니다(73%)"<br />이런식으로 출력해줍니다. (사자, 토끼), (아이유, 아이린) 등 누구와 내가 더 닮았는지 다양한 경우를 제공합니다. | 주      |
| 기능 B | 감정 이모지 | **얼굴인식을 통한 이모지 만들기** [[참조](https://www.ncloud.com/product/aiService/cfr)]<br />셀카를 올리면 얼굴을 가려지기 원하는 사람은 얼굴이 이모지로 대체가 된다.<br />쉽게 프로필 사진이라고 생각하면 됩니다.<br />제공해드린 링크를 보시면 표정에 대한 결과값이 제공되고 그에 맞는 이모지를 프로필로<br />설정해주시면 됩니다. | 서브    |
| 기능 C | 유저 추천   | **활동이나 MBTI기반으로 그룹이나 유저를 추천해주는 기능**<br />MBTI 궁합표 [[참조](https://tailong.tistory.com/314)]를 이용해 빨간색 : 1점, 노란색 : 2점, 연두색 : 3점, 녹색 : 4점, 하늘색 : 5점<br />관심사가 겹칠 때마다 +2점, 좋아요한 글에 대해서 겹칠 때 +0.1점<br />(MBTI + 관심사) * (1 + 좋아요한 게시글 겹칠때마다 0.1씩)<br />유저에 대한 추천은 상위 3명(이름, 프로필)을 추천해준다.<br />유저를 추천해주는 것에서 친구 추가나 쪽지에 대해서는 고려하지 않는다. | 주      |
| 기능 C | 게시글 추천 | **예상 조회수나 추천수를 예측하는 기능**<br />게시글의 메타데이터들을 모아서 글의 길이, 이미지 개수를 고려해 조회수와 추천수를 예측한다. <br />실제 있는 게시판에서 정보를 긁어와 학습하는 것도 좋을 것 같다. | 서브    |

- 각 주차별 팀은 주 기능이 힘들 시 서브 기능을 구현할 수 있다.