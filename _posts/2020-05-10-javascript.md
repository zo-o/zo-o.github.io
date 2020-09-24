---
title: javascript 정리
categories:
 - Algorithm
tags:
 - study
 - javascript
---

<script>

//**********배열복사!!!!!!!!!!!!!!!!!!!!!********************
//주의: @@@배열을 그냥 대입할 경우 참조형 복사@@@@@
///** 참조 없게 2차원배열 복사
check([[0, 0, 0, 1, 1],[0, 0, 0, 1, 0],[0, 1, 0, 1, 1],[1, 1, 0, 0, 1],[0, 0, 0, 0, 0]])
    function check(board){
    //var x=board.slice();

    var x = new Array(board.length);
    for(var i in board){
        x[i] = board[i].slice(0);
    }

    x[0][0]=2;
    console.log(board);
}

//** 참조 없게 1차원배열 복사
var oldArray=[1,2,3];
var newArray=oldArray.slice();


//-------------------------

var money="10000";
 money="-"+money;
 var x= parseInt(money);
 console.log("x"+x);

 var xmon=-10000;
 var ymon=-5000;

 if(xmon>ymon){
     console.log("xmon이 크다");

 }else console.log("wkr");

var a={
    "teo" : 1,
    "ee" : 2
}

console.log(++a.teo);
console.log(a["ee"]);
a["na"]=3;
console.log(a["na"]);

var arr=[];
var arr2=["d","p","b"];
var arr3=["d","a","n"];
arr.push(arr2);
arr.push(arr3);
arr.push(["ddd","bb","ll"]);

arr.sort();


console.log(arr);



var answer=[[]];
answer[0].push(1,2,3);
answer.push([4,5,6]);

console.log(answer);






    ///********Array 클래스********
     //1차원 배열 생성법
    var userName=["a","b","c"];

    console.log(userName);


    //length
    for(var i=0;i<userName.length;i++){
        console.log(userName[i]);     
    }

    //한 배열에 여러가지 타입이 있을 수 있음
   var a=[12,"d","eeee"];

    for(var i=0;i<a.length;i++){
        console.log(a[i]);    
    }

    //2차원 배열 생성법

    var b=[["철수","1","2"],["영희","3","4"]];
    for(var i=0;i<b.length;i++){
        console.log(b[i]);  //["철수","1","2"] ["영희","3","4"]  
    }

    for(var i=0;i<b.length;i++){
        for( var j=0;j<b[i].length;j++){
            console.log(b[i][j]); //철수 1 2 영희 3 4    
        }

    }

    //arr.map() 배열을 반복하고 콜백 함수에서 지정한 return 문을 기반으로 새 배열을 반환
    var nameList = b.map(function(student) {
        return student[0];
    });

    console.log(nameList);

    //arr.filter() 함수의 결과 값을 true 로 만드는 원소로만 구성된 새 배열을 반환한다.
    const adults = b.filter(function(user) {
        return user[1] >= 3;
    });

     console.log(adults);

    var ddd=[];

    console.log("length"+ddd.length);
    //배열 비교 함수 => 배열은 == 으로 비교 안됨 , 비교함수 생성
    var n0=[1,2,3];
    var n1=[3,6,8];
    var n2=[1,2,3];

    function compareArr(a,b){
        for(i=0;i<a.length || i<b.length ; i++){
            if(a[i]!==b[i]) return false
            else continue;
        }
        return true;
    };

    if(compareArr(n0,n1)==true){
        console.log("n0과 n1은 같다");
    }else console.log("n0과 n1은 다르다");

    if(compareArr(n0,n2)==true){
        console.log("n0과 n2은 같다");
    }else console.log("n0과 n2은 다르다");



    //배열이름1.concat(배열이름2) 배열1에 배열2를 합친 배열 반환
    //1차원 배열 합치기
    var c=userName.concat(a);//["a", "b", "c", 12, "d", "eeee"]
    console.log(c);

    //2차원 배열 합치기
    var d=[["나나","3","2"]];
    var f=b.concat(d);
    //0: (3) ["철수", "1", "2"]
    //1: (3) ["영희", "3", "4"]
    //2: (3) ["나나", "3", "2"]

    console.log(f);


    //배열.indexOf(값) 값에 해당하는 배열의 인덱스 반환 없을 경우 -1 반환
    console.log("c의 위치는"+c.indexOf("c")); //2
    console.log("나나의 위치는"+f[2].indexOf("나나")); //0

    //2차원배열의 배열은 indexOf로 찾을 수 없다.
    var a=[["a","v"],["d","d"],[3,4]];
    console.log(a.indexOf(["a","v"]));
    //이런식으로 찾을 수 없음!! 반복문으로 찾을 것
    for(var j=0;j<a.length;j++){

       if(compareArr(a[j],["a","v"])){
           console.log(j); //인덱스
           break;
       }

   }

   //2차원 배열 비교
    var sample=["철수", "1", "2"];

    for(var i=0;i<f.length;i++){
        if(compareArr(f[i],sample)) console.log("철수있다.");
        else console.log("없다");
    }


    //배열 대입
    var sample2=["cd수", "4", "2"];
    sample=sample2;
    console.log(sample);




    //배열.join(구분자) // 배열을 문자열로 합침 구분자가 있을 경우 사이에 넣어줌
    var join_c=c.join('-');
    console.log(join_c); //a-b-c-12-d-eeee

    //배열.pop() 마지막 요소 삭제
    c.pop();
    console.log(c); //["a", "b", "c", 12, "d"]

    //배열.push(값) //배열 마지막에 요소 추가
    c.push("e");
    console.log(c);//["a", "b", "c", 12, "d", "e"]

    //배열.reverse() 배열 뒤집기
    c.reverse();
    console.log(c);//["e", "d", 12, "c", "b", "a"]

    //배열.shift() 첫번째 요소 삭제
    c.shift();
    console.log(c);//["d", 12, "c", "b", "a"]


    //배열.slice(start,end) start번째이상부터 end번째미만까지
    var d=c.slice(0,3); //0인덱스부터 2인덱스 까지 자름
    console.log(d); //["d", 12, "c"]


    //문자배열 정렬하기(기본 오름차순)
    c.sort();
    console.log(c);//[12, "a", "b", "c", "d"]



    //문자배열 정렬하기(내림차순) 문자는 뺄셈이 안되고 대소관계를 비교해야한다.
    c.sort(function(a, b) {
    if (a > b) return -1;
    else if (b > a) return 1;
    else return 0;
});

    console.log(c);//[12, "d", "c", "b", "a"]

    //숫자 정렬
    var number=[1,4,6,18,10,11];
    number.sort();// sort는 아스키코드 순이어서 숫자크기순으로 나오지않는다.
    console.log(number);//[1, 10, 11, 18, 4, 6]

    number.sort(function(a,b){return a-b}); //오름차순 정렬
    console.log(number);///[1, 4, 6, 10, 11, 18]

    number.sort(function(a,b){return b-a}); //내림차순정렬
    console.log(number);//[18, 11, 10, 6, 4, 1]

    //2차원배열 정렬
    f.sort();
    console.log(f);
    //0: (3) ["영희", "3", "2"]
    //1: (3) ["영희", "3", "4"]
    //2: (3) ["철수", "1", "2"]


   //배열.splice() 특정위치에 배열을 추가하거나 삭제
   var item=["a","b","c","d"];
   //베열추가
   item.splice(2,0,"e"); //2번째인덱스에 "e" 추가
   console.log(item);//["a", "b", "e", "c", "d"]
    //배열삭제
    item.splice(0,1); //0번째인덱스부터 1개 삭제
    console.log(item);//["b", "e", "c", "d"]
     item.splice(2,2); //2번째인덱스부터 2개 삭제
    console.log(item);//["b", "e"]



    //배열.unshift(값) 배열 첫번째 요소에 값추가
    item.unshift("a");
    console.log(item);//["a", "b", "e"]


    //*********************함수 사용법

    var c= add(3,4);

    console.log(c);

    function add(a,b){
        return a+b;
    }

    printA();

    function printA(){
        console.log("printA");
    }


    //****형변환***************

    //문자-> 숫자 parseInt(num) parseFloat(num)

    var string_num="5";
    var num=parseInt(string_num);

    console.log(string_num+3); // 53 문자형+숫자형=>문자형
    console.log(num+3);//8

    //숫자 -> 문자 String(num) //기본 정수형
    var num2=5;
    var string_num2=String(num2);

    console.log(string_num2+5); // 55

    //숫자 -> 문자 num.toFixed() //float형 변환
    var floatNum=123.456;
    var float_string=floatNum.toFixed(2); //소수점 2번째까지반올림하여 변환

    console.log(float_string+5); //123.465

    //숫자 -> 문자 num.toString(8), num.toString(16) // 8진수 16진수 변환

    var hexaNum=1234;
    var hexa_string=hexaNum.toString(16);

    console.log(hexa_string+5); //4d25


    //************///<string클래스 사용법>
    //str.charAt(i) str의 i번째 원소 반환
    var name="Yidds"
    for(var i=0;i<name.length;i++){
        console.log(name.charAt(i)); // Y i d d s
    }

    //문자열 합치기
    //str.concat("str2") str뒤에 str2를 합친 문자열을 반환
    var addName=name.concat(" dddd");

    console.log(addName); //Yidds dddd

    //문자열+문자열
    var addName=addName+" cccc"; //Yidds dddd cccc

    console.log(addName);

    //str.indexOf(subtr) str문자열에서 substr이 가장 처음 나오는 위치index를 반환
    var hello= "hello everyone!"
    console.log(hello.indexOf('everyone')); //6
    console.log(hello.indexOf('!')); //14

    //str.lastIndexOf(substr) str문자열에서 substr이 가장 마지막으로 나오는 위치index를 반환
    console.log(hello.lastIndexOf('e')); //13

    //str.replace(str1,str2) str문자열에서 str1을 str2로 변경한 문자열을 반환
    hello=hello.replace('hello','hi');

    console.log(hello); // hi everyone!

    //str.slice(start,end) // 문자열의 start번째이상부터 end번째미만까지 자른 문자열을 반환
    hello=hello.slice(0,4);

    console.log(hello);//hi e

    //str.split(구분자) str을 구분자로 기준으로 나눈 문자열들을 배열형태로 반환
    var rooms="124,566,76,333";

    var room=rooms.split(',');

    console.log(room);

     for(var i=0;i<room.length;i++){
        console.log(room[i]);    //124 566 76 333
    }

    //str.substr(start,count) sstart번째이상부터 count개수 만큼 자른 문자열을 반환
    var abc="abcdefghi";
    var abc2=abc.substr(1,4);

    console.log(abc2); //bcde

    //toLowerCase() 문자열을 모두 소문자로 toUpperCase()  문자열을 모두 대문자로

    var mix="aAbBcC";
    var lower=mix.toLowerCase();
    var upper=mix.toUpperCase();

    console.log(lower); //aabbcc
    console.log(upper); //AABBCC


    //trim() 좌우공백 제거 함수
    var str4="   333   ";
    str4=str4.trim();

    console.log(str4); //333









</script>
