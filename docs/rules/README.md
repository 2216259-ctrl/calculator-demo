---
description: Test-Driven Development (TDD) 규칙
---

# TDD (Test-Driven Development) 규칙

## 개요
이 프로젝트의 **코어 로직**은 TDD 방식으로 구현합니다. UI 관련 코드는 TDD 대상에서 제외됩니다.

## TDD 적용 범위

### ✅ TDD 적용 대상 (코어 로직)
- `Calculator` 클래스 - 기본 계산 로직
- `Scientific` 클래스 - 공학 함수
- `History` 클래스 - 히스토리 관리
- `ExpressionParser` - 수식 파싱
- 유틸리티 함수 (`utils.js`)
- 비즈니스 로직 전반

### ❌ TDD 제외 대상 (UI)
- `Display` 클래스 - DOM 조작
- 이벤트 핸들러
- HTML/CSS 코드
- UI 애니메이션

## TDD 사이클

모든 코어 로직 구현은 다음 순서를 따릅니다:

### 1. Red (실패하는 테스트 작성)
```javascript
// 예시: calculator.test.js
describe('Calculator', () => {
  test('should add two numbers', () => {
    const calc = new Calculator();
    calc.inputNumber('5');
    calc.inputOperator('+');
    calc.inputNumber('3');
    calc.calculate();
    expect(calc.currentValue).toBe('8');
  });
});
```

### 2. Green (테스트를 통과하는 최소한의 코드 작성)
```javascript
// 예시: calculator.js
class Calculator {
  calculate() {
    // 최소한의 구현으로 테스트 통과
    this.currentValue = '8';
  }
}
```

### 3. Refactor (코드 개선)
```javascript
// 예시: calculator.js
class Calculator {
  calculate() {
    // 실제 로직으로 리팩토링
    const a = parseFloat(this.previousValue);
    const b = parseFloat(this.currentValue);
    this.currentValue = String(a + b);
  }
}
```

## 규칙 준수 체크리스트

새로운 코어 로직 기능 추가 시:

- [ ] 테스트를 먼저 작성했는가?
- [ ] 테스트가 실패하는 것을 확인했는가? (Red)
- [ ] 최소한의 코드로 테스트를 통과시켰는가? (Green)
- [ ] 리팩토링 후에도 테스트가 통과하는가? (Refactor)
- [ ] 엣지 케이스를 테스트했는가?
- [ ] 에러 케이스를 테스트했는가?
- [ ] 테스트 커버리지가 90% 이상인가?

## 참고 자료

- [Jest 공식 문서](https://jestjs.io/)
- [Test-Driven Development by Example - Kent Beck](https://www.amazon.com/Test-Driven-Development-Kent-Beck/dp/0321146530)
