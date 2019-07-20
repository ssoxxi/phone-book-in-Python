# phone-book-in-Python, only use very basic grammar
연락처=[] #연락처라는 리스트 선언하여 그 안에 주소록 딕셔너리를 원소로 삽입
주소록={}

#초기화면
print("\n=====WELCOME=====");

#메뉴 선택
#if~else문으로 메뉴 선택을 할 수 있는 기능을 추가
while True:#while문으로 전체 코드를 수용하는 무한루프를 만들어 프로그램 종료까지 실행  
    Keep_P=0
    M=input("\n 0번_전체 연락처 보기\n 1번_저장 2번_검색\n 3번_삭제 4번_종료\n 번호 입력:")
    if M is '0':#변수 M을 선언하여 메뉴입력 번호를 저장
        if len(연락처)==0:#원소의 개수를 확인하는 len()함수로 연락처 리스트에 원소가 없으면 연락처 없음 출력
            print("\n저장 된 연락처가 없습니다.")
        else:
            for a in 연락처:#변수 a선언하여 연락처 리스트에 저장된 모든 정보 출력
                print("\n=====<%s>====="%a['name'])
                print("번호:%s"%a['numb'])
                print("전공:%s"%a['major'])
                print("학번:%s"%a['stunumb'])
        
    elif M is '1':
        #새로운 연락처 저장    
        while True:#두번째 while 무한루프 만들어 저장 기능 실행
            주소록={#주소록 딕셔너리에 input()함수로 새로운 연락처data를 문자형으로 입력
                'name':input("\n[저장]이름을 입력하세요:"),#이름 변수=name
                'numb':input("[저장]번호를 입력하세요:"),#번호 변수=numb
                'major':input("[저장]전공을 입력하세요:"),#전공 변수=major
                'stunumb':input("[저장]학번을 입력하세요:")#학번 변수=stunumb
            }
            연락처.append(주소록)#변수.append()함수 사용하여 새로운data를 뒤에 추가
            keep_S=input("\n계속 저장하시겠습니까? y/n: ")#keep_S변수 선언하여 저장 여부 물음
            if keep_S=='y':#y값이 입력되면 continue문으로 상위 반복문으로 돌아감
                continue
            elif keep_S=='n':#n값이 입력되면 break문으로 루프를 깨줌
                break
    elif M is '2':
        #기존 연락처 검색
        F='y'#변수F값에 'y'문자형 저장
        while F is 'y':#while문으로 변수 F가 y일 때 이하 작업 수행 명령
            addr=input("\n[검색]이름을 입력하세요:")#addr변수 선언하여 새로운 data입력받음
            count=0#count함수 값 0으로 선언
            for dict in 연락처:#for반복문으로 연락처 리스트 검사
                count=count+1#count문에 1씩 증가시켜 전체 원소와 비교하며 입력된 값을 검사
                if (addr==dict['name']):#if문으로 입력된 값이 저장된 값에 있으면 아래 내용 출력
                    print("\n  %s의 번호는 %s입니다."%(dict['name'],dict['numb']))
                    print("  %s의 전공은 %s입니다."%(dict['name'],dict['major']))
                    print("  %s의 학번은 %s입니다."%(dict['name'],dict['stunumb']))
                    break#count비교검사 break문으로 깨줌
                else:
                    if count==len(연락처):#전체 원소와 모두 비교한 수를 카운트하여 count값과 같으면 아래 내용 출력
                       print("\n기존 연락처 명단에 없습니다.") 
            F=input("\n[검색]계속 검색하시겠습니까?y/n:")
                
    elif M is '3':
        #기존 연락처 삭제
        F='y'
        del_a=input("\n전체 연락처를 삭제하시겠습니까?y/n: ")#del_a변수 선언하여 값을 받음        
        if del_a is 'y':
            연락처.clear()#사용자가 y값을 입력하면 변수 del_a에 저장되어 변수.clear()함수를 통해 전체 원소 삭제
            print("\n전체 연락처가 삭제되었습니다.")
            F='n'
        while F is 'y':
            addr=input("\n[삭제]이름을 입력하세요:")#addr변수 선언하여 삭제할 이름 데이터 입력받아 저장
            count=0
            for dict in 연락처:#dict변수 선언하여 for문으로 연락처 리스트의 원소와 비교확인작업 
                count=count+1#count에 1씩 추가하여 차례대로 원소 확인
                if (addr==dict['name']):#if문으로 addr변수에 저장된 값이 연락처 리스트 원소와 일치하는 것을 찾으면
                    del 연락처[count-1]#del 변수함수로 해당 원소 삭제
                    break#해당 원소 삭제했으니 break문으로 삭제 루프 깨줌
                else:
                    if count==len(연락처):#만약 count된 횟수와 연락처의 원소 개수가 같다면 아래 내용 출력
                        print("\n기존 연락처 명단에 없습니다.")
            F=input("\n[삭제]계속 삭제하시겠습니까?y/n:")
    elif M is '4':
        #프로그램 종료
        print("\n프로그램을 종료합니다.\n이용해주셔서 감사합니다.")
        break#break문으로 전체 코드에 적용되던 while루프문 깨줌

    keep_P=input("\n프로그램을 종료하시겠습니까?y/n:") #Keep_P변수에 프로그램 종료에 대한 입력값을 새로 받아 저장
    if keep_P is 'y': #keep_P값이 y라면 아래 내용 출력
        print("\n프로그램을 종료합니다.\n이용해주셔서 감사합니다.")
        break #전체프로그램 종료
