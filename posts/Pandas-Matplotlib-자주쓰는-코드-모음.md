---
title: "[Pandas, Matplotlib] 자주쓰는 코드 모음"
date: 2026-10-15T04:01:35.601Z
tags: ["matplotlib", "pandas", "python"]
velog_slug: Pandas-Matplotlib-자주쓰는-코드-모음
---
### - 앞으로 그리는 그래프 크기를 쭉 고정하려면 | rc
```
plt.rcParams['figure.figsize'] = (12, 6)   # (가로, 세로), 단위는 인치
sns.set_theme(rc={'figure.figsize': (12, 6)}, style='white')
```
### - 그래프 하나만 크기를 바꾸고 싶을 때
```
 plt.figure(figsize=(10, 4))
```

### - 한글 폰트 깨질 때 
```
plt.rc('font', family='Malgun Gothic')   # 윈도우 기본 글꼴이라 경로 없이 이름만
plt.rc('axes', unicode_minus=False)      # 마이너스(-) 기호 깨짐 방지
```
