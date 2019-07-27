##  **Scope** : 어떤 변수들에  접근할 수 있는지 정의하는 것.

>javascript에서 선언 예약어는 각각 var, let, const로 나뉜다.
>
>그리고 let과 const의 경우 block-scope를 var의 경우 function-scope를 지원한다.
>

### **function-scope**

    function foo(){
        for(var i = 0; i <= 10; i++){
            console.log("i",i);
        }
        console.log(i);// i = 10 for block 밖에서도 i를 사용할 수 있다.
    }
    foo();
    console.log(i); // Errorr -> 함수 내부에 선언된 i는 외부에서 사용할 수 없다.

    for(var j = 0; j <= 20; j++){
    	console.log("j",j);
    }
    console.log(j) // 20 -> 함수가 아닌 전역에 선언된 'j' 문제없다.

### **block-scope**
> block '{}' 내부에서 선언된 함수는 외부에서 사용할 수 없다.(if, for, while...)

    for(let bb = 0; bb <= 10; bs++){
    	console.log(bb);
    }
    console.log(bb); //Error bb는 for block 밖에서 사용될 수 없다.
    
    let block = () => {
    	let areaFunction = "function";
    
    	if( 4 %% 2 === 0){
    		let areaIf = "if"
    	}
    	for(let areaFor = 0; areaFor <= 10; areaFor++){
    		if(areaFor === 10){
    			areaFunction = areaFunction + areaFor
    		}
    	}
    	console.log(areaFunction)//"function10"
    	console.log(areaIf)//Error
    	console.log(areaFor) //Error	
    }
    /*
 ### **lexical-scope**