## 개발 환경 🛠
- Unreal Engine 5.1
- C++

## 프로젝트 설명 🗂
Shooter 폴더에 관련 스크립트를 업로드했습니다.

## 소개 링크 🎬
- [Youtube](https://youtu.be/SZlnNw5rXWk)

## 내가 기여한 부분🕹

UI 작업
- UMG (Unreal Motion Graphics) UI 위젯을 코드와 바인딩하여 `인벤토리, 탄약 수, 체력 bar, 데미지`의 정보를 출력

상속 설계 (Weapon, ShooterCharacter)
- 언리얼 엔진의 `Actor` 클래스와 `Character` 클래스를 각각 상속받도록 설계했습니다.
![image](https://github.com/strurao/Space/assets/126440235/64108396-36a6-40cf-9fbb-996c431e8854)

플레이어의 기능 구현 (ShooterCharacter.cpp)
- 전투 기능 (타격 구현, 피격 구현)
- 상태 정보 (총기 없음, 타격, 재장전, 장착 중, 피격) 를 `UENUM(BlueprintType) ECombatState` 으로 구분.
- 매 프레임마다 TraceForItems() 함수로 Weapon 을 수집할 수 있는지 확인하여 Weapon 의 정보 UI를 화면에 띄운다.
- 수집한 `Weapon`을 인벤토리 배열 `TArray<AItem*> Inventory` 에 저장
- `ShooterCharacter`가 소지하고 있는 탄약 정보를 `TMap<EAmmoType, int32> AmmoMap` 에 저장
5 가지의 희귀도를 가진 3 가지의 총기를 2 가지 탄약으로 장전 가능하고, 총기에 따라서 연사가 가능하거나 불가능하도록
- 언리얼 엔진 에디터에서 각 총기 인스턴스를 커스텀할 수 있음
- 이를 위해 언리얼 엔진의 `FTableRowBase` 클래스를 상속받는 커스텀 구조체 `WeaponDataTable` 에 총기 정보를 저장.

![썸넬02](https://github.com/strurao/StarShot/assets/126440235/a916be0f-5e04-4324-bab5-1478fdf5363b)
