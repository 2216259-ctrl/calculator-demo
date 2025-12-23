---
description: SOLID 원칙 준수 가이드
---

# SOLID 원칙

## 개요
이 프로젝트의 모든 코어 로직은 SOLID 원칙을 따라 구현합니다.

---

## S - Single Responsibility Principle (단일 책임 원칙)

### 정의
**하나의 클래스는 하나의 책임만 가져야 한다.**

### 적용 예시

#### ❌ 나쁜 예
```javascript
// Calculator 클래스가 너무 많은 책임을 가짐
class Calculator {
  calculate() { /* 계산 로직 */ }
  saveToHistory() { /* 히스토리 저장 */ }
  updateDisplay() { /* 화면 업데이트 */ }
  formatNumber() { /* 숫자 포맷팅 */ }
}
```

#### ✅ 좋은 예
```javascript
// 각 클래스가 하나의 책임만 가짐
class Calculator {
  calculate() { /* 계산 로직만 */ }
}

class History {
  save(equation, result) { /* 히스토리 저장만 */ }
}

class Display {
  update(value) { /* 화면 업데이트만 */ }
}

class NumberFormatter {
  format(number) { /* 숫자 포맷팅만 */ }
}
```

### 체크리스트
- [ ] 클래스 이름이 하나의 명확한 책임을 나타내는가?
- [ ] 클래스를 변경해야 하는 이유가 하나뿐인가?
- [ ] 메서드들이 모두 클래스의 주 책임과 관련되어 있는가?

---

## O - Open/Closed Principle (개방-폐쇄 원칙)

### 정의
**확장에는 열려있고, 수정에는 닫혀있어야 한다.**

### 적용 예시

#### ❌ 나쁜 예
```javascript
// 새로운 연산 추가 시 기존 코드 수정 필요
class Calculator {
  calculate(a, b, operation) {
    if (operation === '+') return a + b;
    if (operation === '-') return a - b;
    if (operation === '*') return a * b;
    if (operation === '/') return a / b;
    // 새로운 연산 추가 시 이 메서드를 수정해야 함
  }
}
```

#### ✅ 좋은 예
```javascript
// 전략 패턴 사용 - 새로운 연산 추가 시 기존 코드 수정 불필요
class Operation {
  execute(a, b) {
    throw new Error('Must implement execute method');
  }
}

class Addition extends Operation {
  execute(a, b) { return a + b; }
}

class Subtraction extends Operation {
  execute(a, b) { return a - b; }
}

class Multiplication extends Operation {
  execute(a, b) { return a * b; }
}

class Division extends Operation {
  execute(a, b) {
    if (b === 0) throw new Error('Division by zero');
    return a / b;
  }
}

// 새로운 연산 추가 - 기존 코드 수정 없음
class Power extends Operation {
  execute(a, b) { return Math.pow(a, b); }
}

class Calculator {
  constructor() {
    this.operations = new Map([
      ['+', new Addition()],
      ['-', new Subtraction()],
      ['*', new Multiplication()],
      ['/', new Division()],
      ['^', new Power()]
    ]);
  }

  calculate(a, b, operator) {
    const operation = this.operations.get(operator);
    if (!operation) throw new Error('Unknown operation');
    return operation.execute(a, b);
  }
}
```

### 체크리스트
- [ ] 새로운 기능 추가 시 기존 코드를 수정하지 않아도 되는가?
- [ ] 인터페이스나 추상 클래스를 사용하여 확장 가능하게 설계했는가?
- [ ] 전략 패턴, 팩토리 패턴 등을 적절히 활용했는가?

---

## L - Liskov Substitution Principle (리스코프 치환 원칙)

### 정의
**자식 클래스는 부모 클래스를 대체할 수 있어야 한다.**

### 적용 예시

#### ❌ 나쁜 예
```javascript
class ScientificFunction {
  calculate(value) {
    return Math.sin(value);
  }
}

class Logarithm extends ScientificFunction {
  calculate(value) {
    // 부모와 다른 동작 - 음수 입력 시 예외
    if (value <= 0) throw new Error('Invalid input');
    return Math.log(value);
  }
}

// 문제: 부모 클래스 대신 자식 클래스 사용 시 예상치 못한 에러
function processFunction(func, value) {
  return func.calculate(value); // value가 음수면 Logarithm에서만 에러
}
```

#### ✅ 좋은 예
```javascript
class ScientificFunction {
  calculate(value) {
    if (!this.isValidInput(value)) {
      throw new Error('Invalid input');
    }
    return this.compute(value);
  }

  isValidInput(value) {
    return true; // 기본적으로 모든 입력 허용
  }

  compute(value) {
    throw new Error('Must implement compute method');
  }
}

class Sine extends ScientificFunction {
  compute(value) {
    return Math.sin(value);
  }
}

class Logarithm extends ScientificFunction {
  isValidInput(value) {
    return value > 0; // 로그는 양수만 허용
  }

  compute(value) {
    return Math.log(value);
  }
}

// 일관된 동작 - 모든 함수가 동일한 방식으로 에러 처리
function processFunction(func, value) {
  return func.calculate(value); // 모든 함수에서 일관된 동작
}
```

### 체크리스트
- [ ] 자식 클래스가 부모 클래스의 계약을 위반하지 않는가?
- [ ] 자식 클래스가 부모 클래스보다 더 제한적인 전제조건을 요구하지 않는가?
- [ ] 자식 클래스가 부모 클래스보다 더 약한 후속조건을 제공하지 않는가?

---

## I - Interface Segregation Principle (인터페이스 분리 원칙)

### 정의
**클라이언트는 자신이 사용하지 않는 메서드에 의존하지 않아야 한다.**

### 적용 예시

#### ❌ 나쁜 예
```javascript
// 너무 큰 인터페이스
class CalculatorInterface {
  add() {}
  subtract() {}
  multiply() {}
  divide() {}
  sin() {}
  cos() {}
  log() {}
  saveHistory() {}
  loadHistory() {}
  clearHistory() {}
}

// 기본 계산기는 공학 함수와 히스토리 기능이 필요 없음
class BasicCalculator extends CalculatorInterface {
  add() { /* 구현 */ }
  subtract() { /* 구현 */ }
  multiply() { /* 구현 */ }
  divide() { /* 구현 */ }
  
  // 사용하지 않는 메서드들을 억지로 구현해야 함
  sin() { throw new Error('Not supported'); }
  cos() { throw new Error('Not supported'); }
  log() { throw new Error('Not supported'); }
  saveHistory() { throw new Error('Not supported'); }
  loadHistory() { throw new Error('Not supported'); }
  clearHistory() { throw new Error('Not supported'); }
}
```

#### ✅ 좋은 예
```javascript
// 작고 구체적인 인터페이스로 분리
class BasicOperations {
  add(a, b) {}
  subtract(a, b) {}
  multiply(a, b) {}
  divide(a, b) {}
}

class ScientificOperations {
  sin(x) {}
  cos(x) {}
  log(x) {}
}

class HistoryManagement {
  save(entry) {}
  load() {}
  clear() {}
}

// 필요한 인터페이스만 구현
class BasicCalculator extends BasicOperations {
  add(a, b) { return a + b; }
  subtract(a, b) { return a - b; }
  multiply(a, b) { return a * b; }
  divide(a, b) { return a / b; }
}

// 조합을 통해 기능 확장
class ScientificCalculator {
  constructor() {
    this.basic = new BasicCalculator();
    this.scientific = new ScientificOperations();
  }
}
```

### 체크리스트
- [ ] 인터페이스가 단일 목적을 가지는가?
- [ ] 클라이언트가 사용하지 않는 메서드를 구현하도록 강제하지 않는가?
- [ ] 인터페이스가 응집력이 높은가?

---

## D - Dependency Inversion Principle (의존성 역전 원칙)

### 정의
**고수준 모듈은 저수준 모듈에 의존하지 않아야 한다. 둘 다 추상화에 의존해야 한다.**

### 적용 예시

#### ❌ 나쁜 예
```javascript
// 고수준 모듈이 저수준 모듈에 직접 의존
class LocalStorageHistory {
  save(data) {
    localStorage.setItem('history', JSON.stringify(data));
  }
  
  load() {
    return JSON.parse(localStorage.getItem('history') || '[]');
  }
}

class Calculator {
  constructor() {
    // LocalStorageHistory에 직접 의존
    this.history = new LocalStorageHistory();
  }

  calculate(a, b, op) {
    const result = this.performOperation(a, b, op);
    this.history.save({ a, b, op, result });
    return result;
  }
}

// 문제: 다른 저장소(예: IndexedDB)로 변경하려면 Calculator 수정 필요
```

#### ✅ 좋은 예
```javascript
// 추상화 (인터페이스)
class HistoryStorage {
  save(data) {
    throw new Error('Must implement save method');
  }
  
  load() {
    throw new Error('Must implement load method');
  }
}

// 구체적인 구현들
class LocalStorageHistory extends HistoryStorage {
  save(data) {
    localStorage.setItem('history', JSON.stringify(data));
  }
  
  load() {
    return JSON.parse(localStorage.getItem('history') || '[]');
  }
}

class IndexedDBHistory extends HistoryStorage {
  save(data) {
    // IndexedDB 저장 로직
  }
  
  load() {
    // IndexedDB 로드 로직
  }
}

class MemoryHistory extends HistoryStorage {
  constructor() {
    super();
    this.data = [];
  }
  
  save(data) {
    this.data.push(data);
  }
  
  load() {
    return this.data;
  }
}

// 고수준 모듈이 추상화에 의존
class Calculator {
  constructor(historyStorage) {
    // 의존성 주입 - 추상화에 의존
    this.history = historyStorage;
  }

  calculate(a, b, op) {
    const result = this.performOperation(a, b, op);
    this.history.save({ a, b, op, result });
    return result;
  }
}

// 사용
const calc1 = new Calculator(new LocalStorageHistory());
const calc2 = new Calculator(new IndexedDBHistory());
const calc3 = new Calculator(new MemoryHistory()); // 테스트용
```

### 체크리스트
- [ ] 고수준 모듈이 구체적인 구현이 아닌 추상화에 의존하는가?
- [ ] 의존성 주입(Dependency Injection)을 사용하는가?
- [ ] 테스트를 위해 쉽게 모킹(mocking)할 수 있는가?

---

## 프로젝트 적용 가이드

### 클래스 설계 시

1. **단일 책임 확인**
   - 클래스 이름이 명확한가?
   - 변경 이유가 하나뿐인가?

2. **확장성 고려**
   - 새 기능 추가 시 기존 코드 수정이 필요한가?
   - 전략 패턴 등을 활용할 수 있는가?

3. **치환 가능성 검증**
   - 자식 클래스가 부모 클래스를 대체할 수 있는가?
   - 계약을 위반하지 않는가?

4. **인터페이스 분리**
   - 인터페이스가 너무 크지 않은가?
   - 사용하지 않는 메서드를 강제하지 않는가?

5. **의존성 역전**
   - 구체적인 구현에 의존하지 않는가?
   - 의존성 주입을 사용하는가?

### 코드 리뷰 체크리스트

- [ ] 각 클래스가 단일 책임을 가지는가?
- [ ] 새 기능 추가 시 기존 코드 수정이 최소화되는가?
- [ ] 상속 관계가 올바른가?
- [ ] 인터페이스가 적절히 분리되어 있는가?
- [ ] 의존성이 추상화를 향하는가?

---

## 참고 자료

- [Clean Code - Robert C. Martin](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)
- [SOLID Principles of Object-Oriented Design](https://www.digitalocean.com/community/conceptual_articles/s-o-l-i-d-the-first-five-principles-of-object-oriented-design)
- [JavaScript Design Patterns](https://www.patterns.dev/)
