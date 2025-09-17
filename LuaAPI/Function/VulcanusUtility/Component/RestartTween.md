# RestartTween

## 설명
> VulcanusTweener 컴포넌트에 설정되어 있는 데이터를 사용하여 Tween 재 동작을 시작합니다.

## 선언
> vulcanusTweener:RestartTween( )

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |
> Tweener 기능은 객체에 VulcanusTweener 컴포넌트가 추가되어 있어야 합니다.
> ![Tweener](media/images/Tweener.png)

---

## Sample Code
```lua
function this.OnCollisionEnter(collision)
    tweener = thisTransform:GetComponent("VulcanusTweener") 
    tweener:RestartTween()
end
```

