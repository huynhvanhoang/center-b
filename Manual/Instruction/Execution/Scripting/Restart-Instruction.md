# Restart Instruction
같은 Performer 컴퍼넌트 안에 있는 Instruction을 재 실행 합니다.


## Parameter

| **이름** | **설명**                                    |
|--------|-------------------------------------------|
| Target | 반복시키고자 하는 Performer 컴퍼넌트가 있는 오브젝트를 설정합니다. |



## Tip

1. 오브젝트를 설정하는 경우 내부에 있는 Performer 컴퍼넌트만 유효합니다. Trigger 컴퍼넌트 내의 Performer 는 대상으로 인식하지 않습니다.
2. 자신을 등록하는 경우 자신보다 상위에 있는 Instruction을 재 실행의 대상으로 합니다.
3. Instruction을 Loop 시키고자 할 때, 효과적입니다.

