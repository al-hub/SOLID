# SOLID 원칙을 활용한 발명품 경연대회

이 프로젝트는 SOLID 원칙을 설명하기 위한 C++ 예제입니다. 각 원칙을 설명하고, 이를 구현한 코드를 제공합니다. 예제는 발명품 경연대회를 배경으로 하여, 각 원칙을 쉽게 이해할 수 있도록 구성되었습니다.

## 이야기: "SOLID 왕국의 발명품 경연대회"

옛날 옛적, 프로그래밍 왕국에서는 매년 기발한 발명품 경연대회가 열렸습니다. 이번 대회에서는 다섯 명의 용감한 발명가가 각자 특별한 능력을 이용하여 최고의 발명품을 만드는 것이 목표였습니다. 이 흥미진진한 발명 대회 이야기를 통해 SOLID 원칙을 기억할 수 있습니다.

## 1. 단일 책임 원칙 (Single Responsibility Principle, SRP)

단일 책임 원칙은 하나의 클래스는 하나의 책임만 가져야 한다는 원칙입니다.

### 이야기
먼저, 시그리드(Sigrid)가 첫 번째 도전자로 등장했습니다. 그녀는 단일 기능만 수행하는 깔끔한 로봇 청소기를 발명했습니다. 이 로봇은 방 안을 맴돌며 먼지를 빨아들이고, 오직 청소만을 전담했습니다. 시그리드는 로봇이 작은 먼지 하나까지 깨끗이 청소하는 모습을 시연했습니다. 관중들은 단순하지만 강력한 로봇 청소기에 감탄하며 환호했습니다.

### 코드 예시:
```cpp
#include <iostream>

class RobotCleaner {
public:
    void clean() {
        std::cout << "Cleaning the room..." << std::endl;
    }
};
```

## 2. 개방-폐쇄 원칙 (Open-Closed Principle, OCP)
개방-폐쇄 원칙은 소프트웨어 개체는 확장에는 열려 있어야 하지만, 변경에는 닫혀 있어야 한다는 원칙입니다.

이야기
시그리드의 로봇 청소기 시연이 끝난 후, 오스카(Oscar)가 등장했습니다. 그는 기존 로봇 청소기에 새로운 기능을 추가할 수 있는 모듈을 발명했습니다. 오스카는 청소기 본체를 열지 않고도 간단히 부착할 수 있는 공기 청정 모듈을 시연했습니다. 모듈이 추가되자 로봇 청소기는 공기를 정화하며 청소를 계속했습니다. 관중들은 확장 가능성에 큰 박수를 보냈습니다.

### 코드 예시:
```cpp
#include <iostream>

class RobotCleaner {
public:
    void clean() {
        std::cout << "Cleaning the room..." << std::endl;
    }
};

class AirPurifierModule {
private:
    RobotCleaner& robotCleaner;
public:
    AirPurifierModule(RobotCleaner& robotCleaner) : robotCleaner(robotCleaner) {}

    void purifyAndClean() {
        robotCleaner.clean();
        std::cout << "Purifying the air..." << std::endl;
    }
};

```

## 3. 리스코프 치환 원칙 (Liskov Substitution Principle, LSP)
리스코프 치환 원칙은 서브타입은 언제나 자신의 기반 타입으로 교체할 수 있어야 한다는 원칙입니다.

이야기
오스카의 시연이 끝난 후, 리아나(Liana)가 등장했습니다. 그녀는 오스카의 모듈을 사용해 로봇 청소기를 완벽하게 재현하는 로봇을 발명했습니다. 이 로봇은 오스카의 공기 청정 모듈을 그대로 사용하며, 청소와 공기 정화를 모두 수행했습니다. 리아나의 로봇이 기존 청소기와 동일하게 작동하는 모습을 보며 관중들은 놀라움을 금치 못했습니다.

### 코드 예시:
```cpp
#include <iostream>

class RobotCleaner {
public:
    virtual void clean() {
        std::cout << "Cleaning the room..." << std::endl;
    }
};

class AdvancedRobotCleaner : public RobotCleaner {
public:
    void clean() override {
        RobotCleaner::clean();
        std::cout << "Purifying the air..." << std::endl;
    }
};

```

## 4. 인터페이스 분리 원칙 (Interface Segregation Principle, ISP)
인터페이스 분리 원칙은 클라이언트는 자신이 사용하지 않는 인터페이스에 의존하지 않아야 한다는 원칙입니다.

이야기
리아나의 시연이 끝난 후, 이자벨(Isabel)이 등장했습니다. 그녀는 각기 다른 기능을 수행하는 작은 모듈들을 발명했습니다. 이자벨은 청소 모듈, 요리 모듈, 세탁 모듈 등 각각의 기능에 특화된 모듈들을 선보였습니다. 그녀는 청소가 끝난 후 로봇에 요리 모듈을 부착하여 스프를 끓이는 시연을 했습니다. 관중들은 모듈을 쉽게 교체하며 다양한 작업을 수행하는 로봇에 큰 웃음을 터뜨렸습니다.

### 코드 예시:
```cpp
#include <iostream>

class Cleaning {
public:
    virtual void clean() = 0;
};

class Cooking {
public:
    virtual void cook() = 0;
};

class Washing {
public:
    virtual void wash() = 0;
};

class CleaningModule : public Cleaning {
public:
    void clean() override {
        std::cout << "Cleaning the room..." << std::endl;
    }
};

class CookingModule : public Cooking {
public:
    void cook() override {
        std::cout << "Cooking a meal..." << std::endl;
    }
};

class WashingModule : public Washing {
public:
    void wash() override {
        std::cout << "Washing the clothes..." << std::endl;
    }
};

```

## 5. 의존성 역전 원칙 (Dependency Inversion Principle, DIP)
의존성 역전 원칙은 고수준 모듈은 저수준 모듈에 의존해서는 안 되며, 둘 다 추상화에 의존해야 한다는 원칙입니다.

이야기
마지막으로, 데클란(Declan)이 등장했습니다. 그는 모든 모듈이 일관된 규칙에 따라 작동하도록 하는 통합 제어 장치를 발명했습니다. 데클란은 이 장치를 사용해 로봇이 청소, 요리, 세탁 모듈을 자유롭게 교체하며 명령을 수행하도록 시연했습니다. 관중들은 데클란의 제어 장치로 로봇이 완벽하게 작동하는 모습을 보고 환호했습니다.

### 코드 예시:
```cpp
#include <iostream>

class RobotModule {
public:
    virtual void operate() = 0;
};

class CleaningModuleDIP : public RobotModule {
public:
    void operate() override {
        std::cout << "Cleaning the room..." << std::endl;
    }
};

class CookingModuleDIP : public RobotModule {
public:
    void operate() override {
        std::cout << "Cooking a meal..." << std::endl;
    }
};

class WashingModuleDIP : public RobotModule {
public:
    void operate() override {
        std::cout << "Washing the clothes..." << std::endl;
    }
};

class RobotController {
private:
    RobotModule& module;
public:
    RobotController(RobotModule& module) : module(module) {}

    void execute() {
        module.operate();
    }
};

```

## 전체 통합 코드
위의 모든 코드를 하나의 C++ 파일로 통합하여 실행할 수 있습니다.

통합 코드:
```cpp
#include <iostream>

// SRP
class RobotCleaner {
public:
    void clean() {
        std::cout << "Cleaning the room..." << std::endl;
    }
};

// OCP
class AirPurifierModule {
private:
    RobotCleaner& robotCleaner;
public:
    AirPurifierModule(RobotCleaner& robotCleaner) : robotCleaner(robotCleaner) {}

    void purifyAndClean() {
        robotCleaner.clean();
        std::cout << "Purifying the air..." << std::endl;
    }
};

// LSP
class AdvancedRobotCleaner : public RobotCleaner {
public:
    void clean() override {
        RobotCleaner::clean();
        std::cout << "Purifying the air..." << std::endl;
    }
};

// ISP
class Cleaning {
public:
    virtual void clean() = 0;
};

class Cooking {
public:
    virtual void cook() = 0;
};

class Washing {
public:
    virtual void wash() = 0;
};

class CleaningModule : public Cleaning {
public:
    void clean() override {
        std::cout << "Cleaning the room..." << std::endl;
    }
};

class CookingModule : public Cooking {
public:
    void cook() override {
        std::cout << "Cooking a meal..." << std::endl;
    }
};

class WashingModule : public Washing {
public:
    void wash() override {
        std::cout << "Washing the clothes..." << std::endl;
    }
};

// DIP
class RobotModule {
public:
    virtual void operate() = 0;
};

class CleaningModuleDIP : public RobotModule {
public:
    void operate() override {
        std::cout << "Cleaning the room..." << std::endl;
    }
};

class CookingModuleDIP : public RobotModule {
public:
    void operate() override {
        std::cout << "Cooking a meal..." << std::endl;
    }
};

class WashingModuleDIP : public RobotModule {
public:
    void operate() override {
        std::cout << "Washing the clothes..." << std::endl;
    }
};

class RobotController {
private:
    RobotModule& module;
public:
    RobotController(RobotModule& module) : module(module) {}

    void execute() {
        module.operate();
    }
};

// Main function to demonstrate all principles
int main() {
    // SRP
    RobotCleaner robotCleaner;
    robotCleaner.clean();

    // OCP
    AirPurifierModule airPurifierModule(robotCleaner);
    airPurifierModule.purifyAndClean();

    // LSP
    AdvancedRobotCleaner advancedRobot;
    advancedRobot.clean();

    // ISP
    CleaningModule cleaningModule;
    CookingModule cookingModule;
    WashingModule washingModule;

    cleaningModule.clean();
    cookingModule.cook();
    washingModule.wash();

    // DIP
    CleaningModuleDIP cleaningModuleDIP;
    CookingModuleDIP cookingModuleDIP;
    WashingModuleDIP washingModuleDIP;

    RobotController controller(cleaningModuleDIP);
    controller.execute();

    controller = RobotController(cookingModuleDIP);
    controller.execute();

    controller = RobotController(washingModuleDIP);
    controller.execute();

    return 0;
}
```
