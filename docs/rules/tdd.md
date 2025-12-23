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

## 구현 순서

### 1단계: 테스트 먼저 작성
```bash
# 새로운 기능 구현 시
1. 테스트 파일 생성 또는 열기
2. 테스트 케이스 작성
3. 테스트 실행 → 실패 확인 (Red)
```

### 2단계: 구현
```bash
4. 최소한의 코드로 테스트 통과 (Green)
5. 테스트 실행 → 성공 확인
```

### 3단계: 리팩토링
```bash
6. 코드 개선 (Refactor)
7. 테스트 실행 → 여전히 성공하는지 확인
8. 다음 테스트로 이동
```

## 테스트 작성 가이드

### 테스트 구조
```javascript
describe('ClassName', () => {
  // 각 테스트 전에 실행
  beforeEach(() => {
    // 초기화 코드
  });

  // 각 테스트 후에 실행
  afterEach(() => {
    // 정리 코드
  });

  describe('methodName', () => {
    test('should do something when condition', () => {
      // Arrange (준비)
      const instance = new ClassName();
      
      // Act (실행)
      const result = instance.methodName();
      
      // Assert (검증)
      expect(result).toBe(expected);
    });
  });
});
```

### 테스트 네이밍
- **명확하고 구체적으로**: `should return 8 when adding 5 and 3`
- **동작 중심으로**: `should throw error when dividing by zero`
- **조건 명시**: `should return 0.5 when calculating sin(30) in degrees`

### 테스트 커버리지 목표
- **코어 로직**: 90% 이상
- **엣지 케이스**: 모든 경계값 테스트
- **에러 케이스**: 모든 예외 상황 테스트

## 예시: Calculator 클래스 TDD

### Step 1: 테스트 작성
```javascript
// tests/calculator.test.js
import { Calculator } from '../src/calculator.js';

describe('Calculator', () => {
  let calc;

  beforeEach(() => {
    calc = new Calculator();
  });

  describe('Addition', () => {
    test('should add two positive numbers', () => {
      calc.inputNumber('5');
      calc.inputOperator('+');
      calc.inputNumber('3');
      calc.calculate();
      expect(calc.currentValue).toBe('8');
    });

    test('should add negative numbers', () => {
      calc.inputNumber('-5');
      calc.inputOperator('+');
      calc.inputNumber('-3');
      calc.calculate();
      expect(calc.currentValue).toBe('-8');
    });
  });

  describe('Division', () => {
    test('should throw error when dividing by zero', () => {
      calc.inputNumber('5');
      calc.inputOperator('/');
      calc.inputNumber('0');
      calc.calculate();
      expect(calc.currentValue).toBe('Error');
    });
  });
});
```

### Step 2: 구현
```javascript
// src/calculator.js
export class Calculator {
  constructor() {
    this.currentValue = '0';
    this.previousValue = '';
    this.operation = null;
  }

  inputNumber(num) {
    this.currentValue = num;
  }

  inputOperator(op) {
    this.previousValue = this.currentValue;
    this.operation = op;
    this.currentValue = '0';
  }

  calculate() {
    const a = parseFloat(this.previousValue);
    const b = parseFloat(this.currentValue);

    if (this.operation === '/' && b === 0) {
      this.currentValue = 'Error';
      return;
    }

    let result;
    switch (this.operation) {
      case '+': result = a + b; break;
      case '-': result = a - b; break;
      case '*': result = a * b; break;
      case '/': result = a / b; break;
    }

    this.currentValue = String(result);
  }
}
```

## 테스트 실행

### 개발 중
```bash
# 테스트 watch 모드
npm test -- --watch

# 특정 파일만 테스트
npm test calculator.test.js
```

### 커밋 전
```bash
# 모든 테스트 실행
npm test

# 커버리지 확인
npm test -- --coverage
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
- [TDD 실천법과 도구](https://repo.yona.io/doortts/blog/issue/1)
