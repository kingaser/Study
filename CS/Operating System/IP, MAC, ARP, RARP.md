## IP, MAC, ARP, RARP
### IP 주소(Internet Protocol address)
- 논리적 주소
- 컴퓨터 네트워크에서 장치들이 서로를 인식하고 통신을 하기 위해서 사용하는 특수한 번호
- IP를 기반으로 통신한다고도 하지만 사실상 그 밑에 물리적 주소인 MAC 주소를 통해 통신

### MAC 주소(Media Access Control Address)
- 네트워크 인터페이스에 할당된 고유 식별자이며 보통 장치의 NIC에 할당됨
![img.png](../img/img_36.png)
- 48비트로 이루어져있으며 24비트의 OUI와 24비트의 UAA로 이루어져 있음
  - OUI : IEEE에서 할당된 제조사 코드
  - UAA : 제조사에서 구별되는 코드
- MAC주소는 보통 유일하지만 그렇지 않을 수도 있음
- 실수 또는 의도적으로 UAA를 중복되게 만들 수 있음
- 동일 네트워크에서만 중복되지 않으면 문제없음
- NIC에 고정된 MAC주소를 변경할 수는 있으나 하지 않는 것을 권장하며 하는 것 자체를 어렵게 한 OS도 있음

### IEEE(Institute of Electrical Electronics Engineers)
- 전기/전자/전산 분야의 국제 기구 및 학회
- 관련 전문가들이 합병해서 창설한 국제조직이며, 관련 기술 공유와 표준정의 등의 활동

### PC의 NIC
![img_1.png](../img/img_37.png)

### ARP와 RARP
- MAC주소는 ARP를 통해 파악 가능
- ARP를 통해 논리적 주소인 IP 주소를 물리적 주소인 MAC주소로 변환
- 이와는 반대로 RARP를 통해 물리적 주소인 MAC주소를 논리적 주소인 IP주소로 변환하기도 함
![img_2.png](../img/img_38.png)

### ARP의 과정
- 해당 IP주소에 맞는 MAC주소를 찾기 위해 해당 데이터를 브로드캐스팅을 통해 연결된 네트워크에 있는 장치한테 모두 보냄
- 맞는 장치가 있다면 해당 장치는 보낸 장치에게 유니캐스트로 데이터를 전달해 주소를 찾게 됨
![img_3.png](../img/img_39.png)
