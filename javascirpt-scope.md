# Scope
## 1. Scope : 어떤 변수들에  접근할 수 있는지 정의하는 것.

    /*
    var : function-scope
    let, const : block-scope
    */
    
    //-------------------------------------------------------------
    /*
    var의 문제점(?)
    	.net으로 작업을 해오던 나에게 var는 매우 생소했다.
    */
    var a = 0;
    var a = 0;
    //위의 경우 아무 Error가 없다?!
    
    console.log(b); //호이스팅으로 인해 reference error 가 일어나지 않는다?! 
    var b;
    //-------------------------------------------------------------
    
    //function-scope : 함수 내부에서 선언된 변수는 외부에서 사용할 수 없다.
    function foo(){
      for(var i = 0; i <= 10;  i++){
    		console.log("i" , i);
      } 
    }
    foo();
    console.log(i); // Errorr -> 함수 내부에 선언된 i는 외부에서 사용할 수 없다.
    
    for(var j = 0; j <= 20; j++){
    	console.log("j",j);
    }
    console.log(j) // 20 -> 함수가 아닌 전역에 선언된 'j' 문제없다.
    
    //block-scope : block '{}' 내부에서 선언된 함수는 외부에서 사용할 수 없다.(if, for, while...)
    let bs;
    let bs; //중복된 변수선언 Error
    
    console.log(bs); //Null Reference Error
    let bs;
    
    for(let bb = 0; bb <= 10; bs++){
    	console.log(bb);
    }
    console.log(bb); //Null Reference Error
    
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
    lexical-scope : 함수 내부의 정의된 함수는 자신의 부모 함수의 변수를 사용할 수 있다. 반면 부모 함수는
                    자식 함수의 변수를 사용할 수 없다.
    */
    function outerFunction () {
      const outer = 'I’m the outer function!'
        
      function innerFunction() {
         const inner = 'I’m the inner function!'
         console.log(outer) // 자식함수에서 부모함수의 변수 호출 : I’m the outer function!
      }
        
      console.log(inner) // 부모함수에서 자식함수의 변수 호출: Error!!
    }