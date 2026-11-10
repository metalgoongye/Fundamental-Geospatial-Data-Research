# CityGML 3.0 챕터별 핵심 요약

- 대상 문서: OGC 20-010, *OGC City Geography Markup Language (CityGML) Part 1: Conceptual Model Standard*, Version 3.0.0 (2021-09-13 공표, 463쪽)
- 원본 위치: `참고자료\cityGML3.0.pdf`
- 작성: 2026-11-10, 챕터별 5꼭지 내외로 압축. 괄호의 쪽수는 문서 내 쪽번호(표지·목차 제외) 기준.

---

## 1장. Scope — 표준의 범위 (p.2–4)

1. **개념모델(CM) 표준이다.** CityGML 3.0은 가상 3D 도시·경관 모델을 표현하기 위한 **플랫폼 독립 모델(PIM)**로, 특정 기술로 직접 구현하는 대상이 아니라 GML·JSON·DB 스키마 등 **플랫폼 종속 모델(PSM)과 구현표준(Implementation Specification)의 기반**이 된다. 이 문서 자체는 어떤 인코딩도 정의하지 않는다.
2. **적합성 대상은 두 가지.** ① 이 개념모델을 인코딩하는 구현표준, ② 사용자가 이 모델을 확장해 만드는 추가 UML 모델(ADE, 응용도메인확장).
3. **단순 3D 포맷과의 차별점은 시맨틱.** 기하·외관 정보에 더해 풍부한 범용 정보모델(온톨로지)을 갖추고 있어, 다양한 원천 데이터를 하나의 도시모델로 통합하면서 의미적 상호운용성을 보존한다.
4. **대상 응용 분야가 명시돼 있다.** 도시·경관계획, 건축설계, 관광·여가, 환경·에너지·모빌리티 시뮬레이션, 이동통신, 재난관리, 국토안보, 차량·보행자 내비게이션, 훈련 시뮬레이터·모바일 로보틱스.
5. **핵심 특징 목록(3.0 기준).** ISO 19100 계열 기반 정보모델, ISO 19107 기반 3D 기하 + 3D 포인트클라우드, 공간 위계(건물 층 포함) 집계, 외관(텍스처·재질), 시간가변 속성, 실내·외 모두에 적용되는 **LOD 0–3 4단계 다중스케일**(LOD4 폐지), 복수 LOD 동시 표현, 코드리스트·Generic 객체·ADE 3종 확장 수단 — 특히 3.0부터 ADE가 개념 수준의 플랫폼 독립 모델이 되고 서브타이핑 대신 **'hook'으로 속성을 주입**하는 방식을 지원한다.

## 2장. Conformance — 적합성 (p.6–7)

1. **표준화 대상(Standardization Target)은 ① 맞춤형 개념모델(이 CM의 확장판)과 ② 구현표준(이 CM의 인코딩)** 두 종류다.
2. **커뮤니티 맞춤화 방법 4가지:** 선택적 UML 패키지 생략, 속성·연관의 다중도 축소, 속성 허용값 제한, ADE를 통한 개념 추가. 앞의 셋은 구현표준 수준에서 가능하고, 넷째(ADE)만 개념모델 확장을 요한다.
3. **적합성 클래스는 17개**로 UML 패키지(모듈)마다 1개씩 대응하며, 각각 하나의 요구클래스(Requirements Class)로 정의된다. (ADE용 요구클래스 18을 더하면 Annex A의 시험 대상은 19개 부류.)
4. **Core만 필수, 나머지는 선택.** 단, 선택한 적합성 클래스가 다른 클래스에 의존하면 그 의존 클래스도 구현해야 한다.
5. **UML 모델이 정본(正本).** 이 문서는 UML 모델의 문서화 표현이며, 문서와 UML 모델이 불일치하면 UML 모델이 우선한다. 구현표준은 Annex A의 추상 테스트로 적합성 증거를 제시해야 한다.

## 3장. Normative References — 규범 참조 (p.9–10)

1. **ISO 19100 시리즈가 뼈대.** 19107(공간 스키마), 19109(응용스키마 규칙), 19111(좌표참조), 19103(개념스키마 언어 UML), 19123(커버리지), 19108(시간 스키마), 19156(관측·측정), 19101(참조모델), 19105(적합성 시험), 19143(필터 인코딩).
2. **OGC 추상규격·표준:** Topic 5(피처), Topic 8(피처 간 관계), Topic 10(피처 컬렉션), SWE Common, Timeseries Profile of O&M(Dynamizer의 시계열 근거).
3. **모델링 언어 표준:** ISO/IEC 19505-2(OMG UML Superstructure), ISO/IEC 19507(OCL 제약 언어).
4. **그래픽스·주소 표준:** X3D(ISO/IEC 19775-1), Khronos COLLADA(외관 재질 정의의 출처), OASIS xAL v3.0(주소), IETF RFC 2045/2046(MIME)·3986(URI).
5. **유럽 제도 문서 인용:** INSPIRE D2.8.III.2 건물 데이터 명세 기술지침 — 2D/2.5D/3D·LOD 등 용어 정의의 출처로 활용. (국가 공간정보 제도 문서가 국제표준의 규범 참조로 들어간 사례)

## 4장. Terms, Definitions and Abbreviated Terms — 용어 (p.12–17)

1. **요구표현 규약:** OGC Policy Directive 49(ISO/IEC Directives Part 2 기반)와 ModSpec(OGC 08-131r3)을 따르며, 필수 요구는 "shall"로 표기한다.
2. **차원 용어 구분(INSPIRE 출처):** 2D(X,Y), 2.5D(X,Y마다 Z 하나), 3D(완전한 3차원 기하).
3. **모델 위계 용어:** 개념모델(conceptual model) → 개념스키마(그 형식적 기술) → 응용스키마(응용을 위한 개념스키마 집합)의 구분을 명확히 한다.
4. **MDA(모델기반아키텍처) 용어:** 플랫폼, 플랫폼 독립 모델(PIM), 플랫폼 종속 모델(PSM) — 1장의 PIM/PSM 구도의 근거.
5. **기타 핵심 정의와 약어:** 코드리스트(허용값마다 코드를 갖는 값 영역), LOD(실세계를 묘사하는 정보의 양), 생애주기 정보(버전의 시간 특성·버전 간 변경) + BIM·IFC·B-Rep·CSG·DTM·TIN·TIC·GML·WFS 등 약어표.

## 5장. Conventions — 표기 규약 (p.19–23)

1. **규범 조항 식별 URI 체계:** `http://www.opengis.net/spec/CityGML-1/3.0`을 기준으로 모든 요구사항·적합성시험을 상대 URI로 식별한다.
2. **UML 정적 구조 다이어그램**(ISO/TS 19103 표기)으로 모델을 제시하며, **모든 연관(association)은 단방향**이고 화살표로 탐색 방향을 나타낸다.
3. **스테레오타입 체계:** «ApplicationSchema»(모듈=응용스키마), «FeatureType», «TopLevelFeatureType»(도시모델 직속 가능한 최상위 피처), «ObjectType», «DataType», «Enumeration», «CodeList»(허용값 외부 정의·개방형), «Union», «Property», «Version» 등.
4. **색상 규약:** 노랑=해당 절의 요구클래스 소속, 파랑=다른 모듈 소속(패키지명 접두), 초록=ISO 19107/19111/19123 클래스, 회색=ISO 19109의 AnyFeature(모든 피처타입의 메타 상위클래스), 흰색=노트·OCL 제약.
5. **UML 원본 공개:** 전체 다이어그램을 XMI 형식으로 GitHub(opengeospatial/CityGML3-Workspace)에 공개 — 기계가독 정본이 존재한다.

## 6장. Overview of CityGML — 개념 총람 (p.25–44) ★표준 이해의 핵심 장

1. **목적과 위상.** 건물·도로·철도·터널·교량·도시시설물·수체·식생·지형 등 도시공간의 주요 실체를 시맨틱·3D 기하·위상·외관·시간변화 관점에서 저장·교환하는 개방형 모델. 가시화를 넘어 의사결정지원, 스마트시티, 실내외 내비게이션, BIM 통합(준공 문서화), 자율주행, 각종 시뮬레이션이 본령이다.
2. **모듈화 구조.** 필수인 **Core 모듈** + **주제 모듈 11개**(Building, Bridge, Tunnel, Construction[건설 공통], CityFurniture, CityObjectGroup, LandUse, Relief, Transportation, Vegetation, WaterBody) + 모든 주제에 걸치는 **횡단 모듈 5개**(Appearance, PointCloud, Generics, Versioning, Dynamizer). 인코딩·응용은 모듈 부분집합만 지원해도 되고, null mapping으로 특정 요소를 제외할 수 있다.
3. **일반 모델링 원칙.** ISO 19109 피처 개념 기반, 이중 식별자(**featureID**=버전 구분용 필수 / **identifier**=실세계 객체 불변 식별자), **이중시간(bitemporal) 타임스탬프**(creationDate·terminationDate=모델 내 존재기간 + validFrom·validTo=실세계 유효기간)로 도시 전체 이력을 한 데이터셋에 담을 수 있다. 클래스 위계에 따른 속성 상속, TopLevelFeatureType 중심의 집계 위계, 온톨로지 URI로 수식 가능한 관계(relatedTo, 외부참조 등) 지원.
4. **공간 표현.** ISO 19107 기하(B-Rep) 사용, 기하 객체 공유로 위상(인접) 표현(선택적), 동일 형상의 반복 객체를 위한 **ImplicitGeometry**(프로토타입+변환행렬, 씬그래프 개념), 포인트클라우드 표현(LAS/LAZ 참조 가능), 그리고 모든 좌표의 **절대 지오레퍼런싱**(CAD·BIM과의 본질적 차이로, 지구 곡률이 중요한 대형 구조물에 적합).
5. **3.0의 최대 혁신 — 공간(Space) 개념.** 모든 도시객체를 **Space(체적 실체)**와 **SpaceBoundary(면적 실체)**로 정리하고, Space를 물리/논리 공간으로, 물리 공간을 다시 **점유(Occupied: 건물·수목 등)/비점유(Unoccupied: 실내공간·교통공간 등)**로 구분. 기하 표현을 Core로 일원화해 주제 모듈이 단순해지고 LOD 체계가 전 모듈에서 일관화됐다(LOD4 폐지, 실내외 모두 LOD0–3, 시맨틱 분해와 LOD의 분리). 그 밖에 가상 폐합면(ClosureSurface), 지형교차곡선(TIC), 시맨틱-기하 이중 위계의 정합 원칙, 임의 테마(적외선·소음 등)까지 포괄하는 외관(Appearance), 저속 변화용 **Versioning**·고빈도 시계열/센서용 **Dynamizer**, 확장 3수단(Generic, ADE, 코드리스트)을 개관한다.

## 7장. CityGML UML Model — 모듈별 규범 모델 (p.46–159)

1. **구성 방식.** UML 모델이 규범 정의이며, 17개 요구클래스(=UML 패키지)마다 UML 다이어그램 + 클래스 요약표 + 요구사항(REQ)을 제시한다. 이 장이 문서의 본체다.
2. **Core(7.2).** ISO 표준 활용 → 도시모델·도시객체 → 공간 개념 → 기하·LOD → 기타 개념(ImplicitGeometry, ExternalReference, 주소 등) 순으로 7개 절 구성. 모든 공간 표현과 LOD가 여기서만 정의되고 주제 모듈이 이를 상속한다. 각 Space 클래스별 허용 경계면 조합을 표로 규정.
3. **횡단 모듈(7.3, 7.6, 7.7, 7.9, 7.13).** Appearance=재질(X3D·COLLADA 기반)과 텍스처(매개변수화/지오레퍼런스), 테마별·면별 복수 외관. Dynamizer=AtomicTimeseries(시간-값 쌍)·CompositeTimeseries(패턴 합성)·SensorConnection(SensorThings API·SOS·MQTT 등 직결)으로 정적 속성값을 동적으로 덮어씀. Generics=미리 정의되지 않은 공간·면·속성을 4종 Generic 피처와 이름-값 쌍 속성으로 표현(적절한 주제 클래스가 없을 때만 사용). PointCloud=물리공간·주제면의 기하를 점군으로 직접 표현. Versioning=Version(도시모델의 명명된 상태)·VersionTransition(버전 간 변경 사유·내역)을 피처로 다뤄 표준 WFS만으로 버전 관리 가능(git류 워크스페이스 트리 지원).
4. **자연·기반 주제 모듈(7.8, 7.10–7.12, 7.14, 7.4, 7.5).** LandUse=토지이용·토지피복 겸용 면객체. Relief=ReliefFeature 아래 래스터/TIN/브레이크라인/질량점 구성요소 공존. Vegetation=단독식생객체·식생면(PlantCover). WaterBody=수체와 수면(WaterSurface)·수저면 경계. Transportation=Road·Track·Square·Railway·Waterway 5종을 구간(Section)·교차부(Intersection)로 분할하고, 교통공간(TrafficSpace)·보조교통공간과 그 하부 경계인 교통면(차로·보도 등)·보조교통면(연석·녹지대 등), 선택적 여유공간(ClearanceSpace)까지 표현 — 전체 면→차로→주행로 수준의 세분화(granularity) 지원. CityFurniture=도로표지·가로등 등 소형 고정 시설물. CityObjectGroup=역할 부여가 가능한 사용자 정의(재귀적) 그룹.
5. **건설 계열 모듈(7.15–7.18).** Construction이 건물·교량·터널의 공통 개념(설치물 Installation/가구 Furniture/구성요소 ConstructiveElement, 벽·지붕·바닥 등 경계면 체계, 창·문 개구부와 충전요소, 기타구조물 OtherConstruction)을 정의하고, **Building**(BuildingPart 물리 분할 + Storey·BuildingUnit 논리 분할 + Room 실내), **Bridge**(BridgePart, 주탑·케이블 등 구조요소, BridgeRoom), **Tunnel**(TunnelPart, HollowSpace)이 이를 상속·특화한다.

## 8장. CityGML Data Dictionary — 데이터 사전 (p.161–366)

1. **UML 모델에서 소프트웨어로 자동 생성한 정규 데이터 사전**으로, 7장과 함께 개념모델의 또 하나의 규범적 표현이다(206쪽 분량, 문서의 절반).
2. **클래스마다 메타데이터 표** 하나씩: 정의(DEFINITION), 상위클래스, 스테레오타입, 그리고 속성·연관의 이름/정의/타입/다중도.
3. **ISO 클래스 먼저(8.1).** AnyFeature(ISO 19109) 등 CityGML이 가져다 쓰는 ISO 클래스를 정의한 뒤, 8.2~8.18에서 Core부터 Tunnel까지 모듈별로 수록한다.
4. **모듈별로 피처타입 → 데이터타입 → 코드리스트 → 열거형 순**으로 정리되며, 각 피처타입의 ADE 확장 고리인 `ADEOf<피처타입명>` 데이터타입("hook")도 모두 수록된다.
5. **코드리스트는 값을 문서에 넣지 않는다.** 허용값은 외부 레지스터에서 정의하도록 하여(개방형), 국가·산업 분류체계를 그대로 연계할 수 있는 지점을 만들어 둔다. — 사전 전체가 용어·속성 수준의 제도화(표준 사양서) 모범 사례.

## 9장. Application Domain Extension (ADE) — 확장 메커니즘 (p.368–374)

1. **ADE = 특정 응용·도메인을 위한 공식적·체계적 확장**을 UML 개념모델로 정의한 것. Generic 객체·속성과 달리 형식 스키마가 있어 **검증(validation)이 가능**하며, 3.0부터는 XML 스키마 수준이 아닌 **개념 수준의 플랫폼 독립 모델**이 되어 여러 인코딩으로 매핑된다. (대표 사례: Utility Network ADE, Energy ADE)
2. **일반 규칙:** ISO 19109 일반피처모델과 ISO 19103 UML 규칙을 따르고, 전역 고유 네임스페이스를 갖는 UML 패키지로 조직한다(REQ 48).
3. **새 피처타입 정의 규칙:** 모든 ADE 피처타입은 Core::AbstractFeature(공간 객체면 AbstractSpace/AbstractSpaceBoundary)에서 직·간접 파생해야 하며, 이로써 공간 표현·LOD 개념을 자동 상속한다. 최상위 피처는 «TopLevelFeatureType» 표기, 새 공간속성이 LOD에 속하면 이름을 `lodX` 접두로 시작(REQ 49).
4. **Hook 메커니즘(3.0 신설):** 서브클래싱 대신, 모든 CityGML 피처타입에 내장된 `adeOf<피처타입명>` 속성(타입 `ADEOf<피처타입명>`)의 **서브 데이터타입을 만들어 속성을 주입**한다(REQ 50). 복수 ADE가 같은 피처 인스턴스에 동시 적용될 수 있고, 모르는 ADE 내용은 무시하면 되며, ADE의 ADE도 가능하다. 서브클래싱보다 hook 사용이 권장된다.
5. **인코딩은 별도 표준에 위임.** 이 장은 개념 모델링만 다루고, ADE를 특정 인코딩으로 매핑하는 규칙은 해당 CityGML 인코딩 표준이 정의한다. 요구클래스 18(대상: 개념모델)로 묶인 요구사항 48–50과 권고 1–2가 규범의 전부로, 간결한 확장 거버넌스를 보여준다.

## 부속서 (p.376 이하)

- **Annex A(규범) 추상 테스트 수트:** 19개 적합성 클래스(Core~Tunnel + ADE)별로 "구현표준이 개념모델의 클래스·관계·속성을 동일하게 구현했는가"를 **수동 검사**하는 시험 방법을 규정. 개념모델 표준이라 실행형 테스트 스크립트는 불가능함을 명시.
- **Annex B(참고) 개정 이력**, **Annex C(규범) 용어집**(일반 용어 + ISO 개념), **참고문헌** 순.

---

## 본 연구와의 접점 메모 (요약자 주)

1. **PIM/PSM 분리 설계**: 기본공간정보 데이터모델도 개념모델(제도화 대상)과 인코딩(GML/JSON/DB)을 분리하면 기술 변화에 견디는 표준이 된다 — CityGML 3.0이 1~2장에서 보여주는 구도.
2. **Core 필수 + 모듈 선택 구조**: "전부 구현"을 강제하지 않는 적합성 설계가 보급·제도화의 현실적 장치.
3. **Space/SpaceBoundary 시맨틱 일원화**: 기하를 Core로 모으고 주제 클래스는 의미만 정의하는 방식은 AI 활용(온톨로지화, 추론, 검증 자동화)에 유리한 구조.
4. **확장 거버넌스 3단계**(코드리스트 → Generic → ADE)와 hook 메커니즘: 국가 데이터모델에 부처·지자체·민간 확장을 수용하는 제도 설계의 참조 모델.
5. **이중시간 이력 + Versioning/Dynamizer**: 기본공간정보의 갱신·이력 관리와 센서(IoT) 연계를 데이터모델 수준에서 규정한 선례.
