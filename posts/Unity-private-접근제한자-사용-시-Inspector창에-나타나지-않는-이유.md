---
title: "[Unity] private 접근제한자 사용 시 Inspector창에 나타나지 않는 이유(SerializeFiled)"
date: 2024-10-08T16:56:05.539Z
tags: ["SerializeFiled", "Unity"]
velog_slug: Unity-private-접근제한자-사용-시-Inspector창에-나타나지-않는-이유
---
# SerializeFiled
유니티에서 [SerializeField]를 사용하는 주된 이유는 프라이빗(private) 변수를 인스펙터(Inspector)에서 편집할 수 있도록 하기 위함이다. 이를 통해 코드의 캡슐화를 유지하면서도, Unity 에디터에서 변수를 쉽게 설정할 수 있다.

---

## [SerializeField]를 사용하는 이유:
### 프라이빗 변수의 유지
Unity에서 public 변수를 인스펙터에서 자동으로 노출해 주지만, public으로 만들면 그 변수가 코드의 다른 클래스나 스크립트에서 접근 가능해진다. 하지만 일부 변수는 외부에서 접근할 필요가 없고, 오직 인스펙터에서만 편집할 수 있도록 하고 싶을 때, [SerializeField]를 사용해 private 변수로 유지하면서 인스펙터에서 노출할 수 있다.

### 캡슐화와 코드 보호
변수는 보통 캡슐화의 원칙에 따라 private으로 선언되어 외부 접근을 제한하는 것이 좋다. 이렇게 하면 코드의 안정성과 유지보수성이 높아지는데, 동시에 Unity의 인스펙터에서 변수의 값을 손쉽게 설정할 수 있도록 하려면 [SerializeField] 속성이 유용하다.

## [SerializeField]를 사용하는 경우
### 디자인 또는 설정 값을 조정해야 하는 경우
개발 중에 변수 값이 자주 바뀔 수 있는데, 매번 코드에서 값을 수정하지 않고 Unity 에디터의 인스펙터에서 손쉽게 수정할 수 있게 할 때 사용합니다.

### 프로그래밍 논리에 영향을 주지 않으면서 변수 값만 조정하고 싶을 때
게임 오브젝트의 스피드, HP, 색상 등 자주 변경되지만 다른 클래스에서 접근할 필요는 없는 설정 값을 인스펙터에서 노출시켜 조정하는 경우.

----
### 예시 1
```
public class Player : MonoBehaviour
{
    [SerializeField] 
    private int health = 100;

    [SerializeField]
    private float speed = 5.0f;

    private void Update()
    {
        // 플레이어 이동 처리
    }
}
```
위 코드에서 health와 speed는 private 변수이지만, [SerializeField] 속성을 사용해 Unity 인스펙터에서 값을 설정할 수 있다.

---

### 예시2 (유니티 인스펙터)

```
private ParticleSystem FlashEffect; // 총 발사 파티클
private ParticleSystem ShellEffect; // 총알 떨어지는 파티클

```
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/85143dc99973a8ce.png)
(인스펙터에 안뜨는 문제 발생..)

private를 스크립트에 작성 했는데 Inspector창에 뜨지 않는다.
그 이유는 
private접근제한자 때문인데, Unity의 Inspector에서는 public으로 선언된 변수 또는 [SerializeField] 어트리뷰트를 사용한 private 변수가 표시된다. 

그래서 위 코드의 경우 이렇게 수정할 수 있다.
```
//방법1 [SerializeField] 어트리뷰트 사용
[SerializeField] private ParticleSystem FlashEffect; // 총 발사 파티클
[SerializeField] private ParticleSystem ShellEffect; // 총알 떨어지는 파티클

//방법2 변수를 public으로 선언
public ParticleSystem FlashEffect; // 총 발사 파티클
public ParticleSystem ShellEffect; // 총알 떨어지는 파티클


```

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/4ced9af37c65176c.png)

코드를 수정해주니 잘 보인다.