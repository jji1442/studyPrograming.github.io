[24.07.17 ~ 24.07.23]
Q1. namespace vs. class.
namespace:
	1. 전역 접근 가능.
		namespace에서 정의된 변수나 함수는 "#include" 지시어 없이도(헤더파일 없이도) 외부 스크립트에서 접근할 수 있음.
		namespace의 멤버는 기본적으로 public으로 사용되며, 접근제어자를 설정할 수 없음.
		namespace의 멤버로 class와 struct를 정의할 수 있으며, class와 struct의 멤버는 접근제어자를 설정할 수 있음.
	2. 객체화 불가능.
		namespace 자체는 객체 생성이 불가능하나, 객체를 생성할 수 있는 class나 struct는 객체 생성이 가능함.
		객체를 생성할 필요없을 때, namespace를 사용함.
class:
	1. 정의된 범위 내에서 접근 가능.
		class는 정의된 범위 내에서 접근할 수 있음.
		class의 접근제어자에 따라 class의 멤버 변수와 메소드에 대한 접근 권한이 제어됨.
		이는 class가 정의된 범위 내에서만 멤버에 접근할 수 있게 데이터 은닉함.
	2. 객체화 가능.
		객체를 생성함으로써, 객체를 통해 class 멤버에 접근하고 조작할 수 있음.
		class의 static 멤버는 객체를 생성하지 않아도, class의 static 멤버에 접근하고 조작할 수 있음.

Q1-1. 헤더파일을 사용하는 이유?
1. 컴파일 시간 단축.
	파일을 include할 때, 파일 전체를 컴파일함.
	헤더파일이 메인파일의 위치를 참조하고 있어 컴파일 시간을 단축할 수 있음.
2. 재사용 용이성.
	모듈화된 코드는 독립적인 기능 단위로 분리되어 있어서,
	다른 프로젝트나 다른 파일에서 쉽게 재사용할 수 있음.

Q1-2. 함수(function) vs. 메소드(method).
함수(function):
	특정 작업을 수행하는 코드 블록.
	이름을 가지고 있으며, 호출될 때 특정 작업을 수행하고, 필요에 따라 값을 반환함.
	일반적으로 class나 객체에 속하지 않음.
메소드(method):
	class 또는 객체에 속한 함수.
	class의 멤버 변수에 접근할 수 있으며, 객체의 상태를 변경하거나 특정 작업을 수행하는 데 사용.

Q1-3. struct vs. class.
struct:
	1. 기본/상속 접근 제어자 - public.
	2. 역사.
		C언어에서 struct는 데이터와 관련된 멤버 변수만을 가질 수 있었지만, 멤버 함수는 정의할 수 없었음.
		C++언어에서는 struct는 멤버 함수, 멤버 변수 둘 다 가질 수 있음. 상속과 다형성 같은 객체 지향 프로그래밍 개념을 지원함.
class:
	1. 기본/상속 접근 제어자 - private.
	2. 역사.
		C언어에서는 존재하지 않았음.
		C++언어에서 class는 멤버 함수, 멤버 변수 둘 다 가짐. 상속과 다형성 같은 객체 지향 프로그래밍 개념을 지원함.

Q1-3-1. C++언어로 넘어오면서 struct는 멤버 함수 및 객체지향 시스템을 가지게 한 이유는? vvvvvvvvvvvv


Q1-4. 인스턴스 vs. 객체(feat. 객체화).
인스턴스:
	class에서 생성된 실체.
객체(object):
	class의 인스턴스.
-> 인스턴스와 객체(object)는 서로 유사하다고 봐도 무방함.
객체화:
	추상적인 class 설계로부터 구체적인 객체를 생성하는 과정.

Q1-4-1. 유니티 용어와의 구분(feat. 오브젝트, 인스턴스화).
오브젝트(object):
	유니티의 게임 속 모든 물체 또는 요소(컴포넌트, 리소스)를 지칭하는 포괄적인 용어.
인스턴스화:
	유니티에서 프리팹화된 오브젝트를 실체화하는 과정.

Q1-4-2. 객체를 생성하는 방식?
1. Test test;
	스택 메모리에 할당되며, 범위를 벗어나면 자동으로 소멸함.
2. Test test = new Test();
	힙 메모리에 할당되며, 범위를 벗어나도 남아있음.
	delete 연산자로 없애주지 않으면, 프로그램 실행 동안 메모리 누수가 일어남.
	프로그램 종료 시, 자동으로 메모리가 회수됨.

Q1-5. static vs. public.
static:
	class, struct 또는 함수의 멤버가 class나 struct의 객체에 종속되지 않기 위한 키워드.
	함수 내에서 사용 시, 처음 호출될 때만 한 번 초기화된 후, 프로그램이 종료될 때까지 그 값을 유지함.
	class, struct 이름을 통해 접근 가능하며, 객체 없이도 사용하지만, 다른 모든 객체에 영향을 줌.
public:
	class, struct 또는 함수의 멤버가 class나 struct의 객체에 종속되는 키워드.
	함수 내에서 사용 시, 함수 호출될 때만 존재하며, 함수 종료되면 소멸됨.
	특정 객체에 속하므로, 객체를 생성한 후에야 접근 가능.

Q1-6. 다형성?
1. 정적 다형성(함수 오버로딩, 템플릿).
	어떤 함수를 사용할 것인지 컴파일 타임에서 바로 결정이 가능해 런타임 오버헤드가 존재하지 않음.
2. 동적 다형성(함수 오버라이딩, 인터페이스).
	어떤 함수를 사용할 것인지 컴파일 타임에서 바로 결정이 불가능해
	런타임에서 직접 실행시켜 어떤 함수를 사용할 것인지 확인해야하므로
	약간의 런타임 오버헤드가 존재함.

Q1-6-1. 컴파일 타임 vs. 런타임 vs. 런타임 오버헤드.
컴파일타임:
	프로그램의 소스코드가 컴파일러에 의해 실행이 가능한 형태(기계어로 변환)되는 시점.
런타임:
	컴파일 타임이 완료된 후, 프로그램이 실제로 실행되는 시점.
런타임 오버헤드:
	지연시간.

Q1-6-2. interface(feat. 시그니처)?
interface:
	class가 "반드시" 구현해야 할 요소들의 모음.
	method 작성할 때, 헤더파일처럼 시그니처를 사용함.
	시그니처는 메소드이름과 매개변수, 리턴값만 작성함을 의미함.
	부모 클래스가 필요 없으며 다형성을 활용해야 할 때, interface를 활용함.

Q1-6-2-1. 다중구현(interface) vs. 다중상속(class).
다중구현:
	멤버이름 충돌문제.
다중상속:
	상속받은 부모 클래스들 중 조부모 클래스가 같을 경우,
	모호성으로 인해 원하는 결과되지 않을 수 있음.

Q1-7. 캡슐화?
1. 데이터 보호(setter 함수, getter 함수).
	내부 데이터를 보호하고, 무결성을 유지함.
	(setter 함수: 데이터 확인 및 멤버 값 변경, getter 함수: 멤버 값 제공)
2. 데이터 은닉(interface).
	내부 데이터는 숨기고, 외부에 필요한 멤버들은 interface만 노출하여 유지보수성과 확정성을 높힘.

Q1-7-1. 캡슐화의 데이터 은닉: 캡슐화의 장점 vs. interface의 장점? vvvvvvvvvvvv
