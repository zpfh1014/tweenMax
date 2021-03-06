# tweenMax

link : [tweenMax](https://greensock.com/docs/v2/TweenMax)



## 기본 탬플릿

### .to()

```
TweenMax.to(target, duration, {vars});
```
1. **to** : target에 적용된 값으로 모션 이동,  max의 최종 지점
2. **target** : Object - 대상
3. **duration** : Number - 지속시간 (몇초동안 진행되는 시간)
4. **vars(variables)** : Object - 객체의 모든 속성


### .from()

```
TweenMax.from(target, duration, {vars});
```
- max의 시작 지점


### .fromTo()
- 두가지 애니메이션 값을 주어 from에 지정된 값 -> to에 지정된 값으로 애니메이션이 보여지게 한다.


### .allTo() / .allFrom()
- for문 없이 여러 target을 동시에 적용

```
TweenMax.allTo([mc1, mc2, mc3, mc4, mc5], 1, {y:"100", alpha:0, delayIncrement:0.2});
```
- delayIncrement : Number - 각 target들 간에 delay


### .staggerTo() / .staggerFrom()
- target이 배열 속성으로, 각 요소를 순차적으로 모션 호출

```
TweenMax.staggerFrom(".box", 1, {
  ease: Back.easeOut,
  opacity : 0,
  y: 200,
  delay: 0.5,
	onComplete: completeHandler, 
	onCompleteParams: ["{self}"]
}, 0.2);

var $console = $('#console')

function completeHandler(tween){
	$console.append("<p> tween complete / target text = " + tween.target.innerHTML + "</p>")
}
```

1. **onComplete** : Function - 애니메이션이 완료될 때 호출되는 함수
2. **onCompleteParams** : Array - 함수를 전달할 매개 변수의 배열
  ex) onCompleteParams: [element, "param2"]
  매개 변수중 하나에서 트윈맥스 자체 참조하려면 {self}로 쓰면 됨.
  
3. **onCompleteAll** : Function - 전체 트윈 시퀀스가 완료될 때 호출되어야하는 함수, 한번만 호출
4. **onCompleteAllParams** : Array - 메서드를 전달할 매개 변수의 배열


### .TimelineMax()

```
var timeLine = new TimelineMax(); 
timeLine.to($('.box'), 1, {backgroundColor: '#ccc'}) 
        .to($('.box2'), 1, {backgroundColor: '#54c0c7'}) 
        .to($('.box'), 1, {backgroundColor: '#000'}) 
        .to($('.box3'), 1, {backgroundColor: '#54c0c7'});
```
- 하나의 애니메이션이 아닌, 타임라인식으로 애니메이션 모션 





## 모션 제어


### repeat

- 반복구문이며 number은 1부터 시작이다.(1은 무한반복)
- delay가 있는 경우 첫번째 재생만 delay가 적용되고 repeat되는 동안은 delay가 적용되지 않는다.
- **repeatDelay()** : 반복 지연시간을 초 단위로 지정할 수 있다.

```
TweenMax.to(".box", 1, {backgroundColor: '#54c0c7',repeat: 1});

var tween = TweenMax.to(".box", 1, {backgroundColor: '#54c0c7'});
tween.repeat(1);
```


### 기타

**1. yoyo**
- Boolean, 애니메이션을 앞뒤로 반복하여 실행시킨다.
- yoyo 를 사용하기 위해서는 반드시 repeat 필요

```
TweenMax.to(".box", 1, {padding: 20, repeat: 1, yoyo: true});
```

**2. reverse / .reversed**
- 애니메이션 재생, 역재생에 대한 여부 및 설정

**3. isActive**
- 애니메이션 활성화 여부

```
document.querySelector("#tweenBox").addEventListener("click", function() {
  if(!tween.isActive()) {
    // Only reverse the direction if the tween is not active
    tween.reversed() ? tween.play() : tween.reverse();
  }
});
```


###  kill 관련

1. **TweenMax.killAll()** : 전체 트윈 기능 없앰

2. **TweenMax.killDelayedCallsTo(function:Function)** : 해당 delayedCall함수를 kill 함
 
3. **TweenMax.killAllTweens(complete:Boolean):void** :
 - false(default) : pause() 처럼 보이면서 tween kill
 - true : complete 화면을 보여주고 tween kill
 - delayedCall은 kill안됨
 
4. **pause()** : void, 현재 위치에서 일시 중지 

5. **paused()** : void, 애니메이션이 현재 일시 중지 되었는지에 대한 여부 및 설정

6. **resume()** : (suppressEvents : Boolean) 방향을 바꾸지 않고 재생을 계속한다.


## VARIABLES

link : [link](https://greensock.com/docs/v2/TweenMax/vars)



## Easing

link : [link](https://greensock.com/docs/v2/Easing)


## gsap plugin

https://greensock.com/docs/v3/Plugins/ScrollTrigger


