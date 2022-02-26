# Go
2009년 구글에서 개발한 프로그래밍 언어.
GoRoutine을 이용한 병렬 실행이 특징.

# 문법
## 변수 / 상수 선언
```go
(변수 종류) (변수명) (변수 타입) = (변수 값)
var name string = "leti"
const myAge int = "20"
```

함수 내에서 사용 가능한 다른 방법
``` go
name := "leti" // go가 string 으로 타입 추론
```

## 함수
``` go
func 함수명(파라미터 파라미터의 타입) return 값 타입 {
    return 값
}

// 파라미터 전부 같은 타입이면 끝에 한번만 적어도 됨
func multiply (a, b int) int {
    return a * b
}

// func은 여러개의 return value를 가질 수 있음
func lenAndUpper(name string) (int, string) {
    return len(name), strings.ToUpper(name) // 대문자로 변환
}

// 여러개 return value를 가져오기
func main() {
    totalLength, upperName := lenAndUpper("leti")
    // return value에서 필요없는 값은 _로 알려주면됨
    _, upperName := lenAndUpper("leti")
}

// 여러개 파라미터 받기
func repeatMe(words ...string) {
    fmt.Println(words)
}

func main() {
    repeatMe("leti", "nico", "umm", "nice")
}

// naked function
// return value를 미리 알려주는 방식
func lenAndUpper(name string) (length int, uppercase string) {
    length = len(name)
    uppercase = strings.ToUpper(name)
    return 
}

// defer : function의 작동이 끝나면 다른 것을 실행시키는 명령어
func lenAndUpper(name string) (int, string) {
    defer fmt.Println("I'm done") // return 하고 "I'm done" 출력시킴
    return len(name), strings.ToUpper(name)
}
```

## for
``` go
func superAdd(numbers ...int) int {
    // for (n번째), (값) := range (반복할 값)
    for index, number := range numbers {
        fmt.Println(index, number)
    }

    // _로 무시 가능
    for _, number := range numbers {
        fmt.Println(number)
    }

    // c++ 방식
    for i := 0; i < len(numbers); i++ {
        fmt.Println(number)
    }
    return 1
}

func main() {
    superAdd(1, 2, 3, 4, 5, 6)
}
```

## if
``` go
func canIDrink(age int) bool {
    if age < 18 {
        return false
    }
    return true
    
    // variable expression : if를 쓰는 순간 variable를 생성할 수 있음
    // if-else문에만 쓰인다는 명확성도 있음
    if korean_age := age + 2; korean_age < 18 {
        return false
    }
    return true
}
```

## switch
``` go
// C++ switch-case와 비슷
func canIDrink(age int) bool {
    // variable expression 가능
    switch koreanAge := age + 2; koreanAge {
    case 17:
        return false
    case 18:
        return true
    }
    return false

    // 이렇게도 가능
    switch koreanAge := age + 2; {
    case koreanAge < 18:
        return false
    case koreanAge >= 18:
        return true
    }
    return false
}
```

## pointer
``` go
a := 2
b := &b // b는 a의 주소값을 가지는 pointer
fmt.Println(a, *b) // *b : a주소에 저장된 값을 출력

// 그러므로 a의 값을 바꾸면 a의 주소를 가르키는 b의 값도 바뀜
a = 3
fmt.Println(*b) // 3
```

## array, slice
``` go
// array는 길이제한 있음
names := [5]string{"leti", "nico", "umm"}
names[3] := "ok"
names[4] := "ok"
names[5] := "error" // names의 크기를 초과하는 index여서 불가능

// slice는 길이제한이 없음
names := []string{"leti", "nico", "umm"}
names = append(names, "meme") // 값 추가
```

## map
```go
// python으로 치면 dictionary를 담는 array인데 key와 value 타입이 정해짐
nico := map[string]string{"name":"nico"}
nico["address"] = "seoul" // 값 추가
```

## struct
go는 class, constructor method 없음
```go
// type (struct이름) struct 
type person struct {
    name    string
    age     int
    favFood []string
}

func main() {
    favFood := []string{"kimchi", "ramen"}
    nico := person{"nico", 18,favFood}
    me := person{name: "leti", age: 20, favFood: favFood}
    fmt.Println(me.name)
}
```