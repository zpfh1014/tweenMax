# tweenmax


```
TweenMax.to( target, 1, { x:200, y:200, rotation:360, alpha:0, tint:0 } );
```

1. **to** : target에 적용된 값으로 모션 이동
2. **target** : TweenMax.to의 대상이 되는 object
3. **1** : duration, 트윈이 진행되는 시간
4. { x:200, y:200, rotation:360, alpha:0, tint:0 } : 기타 속성, tint : 16진수 값에 해당하는 색상


```
TweenMax.from( target, 1, { x:200, y:200, rotation:360, alpha:0, tint:0 } );
```

1. **from** : 적용값을 초기값으로 적용하여 이동된 상태에서 원래 상태로 되돌아오는 모션



## 기타 속성

1. **yoyo** : 
