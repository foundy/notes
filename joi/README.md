# Joi validator
> Object schema description language and validator for JavaScript objects.

* [github.com/hapijs/joi](https://github.com/hapijs/joi)

## Table of Contents
* [extension](#extension)

## References

---

## extension

### parameters
* `name`: 사용자 정의 타입 명. (필수)
* `base`: 사용자 정의 타입의 베이스를 지정. 기본값 `Joi.any()`.
* `coerce`: `base` 이전에 실행되는 함수. 다른 유형의 값을 강제 변환하려는 경우에 사용.
* `pre`: 유효성 검사 체인의 첫 번째 실행되는 선택 함수는 일반적으로 값을 캐스팅 하는 경우 사용. `value`, `state`, `options` 3가지 인수를 받음.
* `language`: 오류 정의를 추가. 모든 키에 타입 명이 붙음.
* `describe`: 완료된 설명을 후 처리.
* `rules`: 추가할 룰의 배열.
  * `name`: 신규 룰의 명. (필수)
  * `params`: 각 파라미터의 Joi 스키마를 포함. Joi.object()이면 단일 Joi 스키마를 전달할 수 있음. 물론 `pattern` 이나 `rename` 같은 일부 메소드는 유효하지 않거나, 컨텍스트에서 동작하지 않을 수 있음.
  * `setup`: 룰을 설정할 때 스키마의 내부 조작을 허용하기 위해 제공되는 파라미터를 사용하여 설정. 적어도 `setup` 이나 `validate`는 반드시 제공되어야 함.
  * `validate`: `params`, `value`, `state`, `options` 파라미터 값 유효성 검사. 적어도 `setup` 이나 `validate`는 반드시 제공되어야 함.
  * `description`: 룰을 설명.
