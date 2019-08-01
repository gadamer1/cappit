## 1. javascript acmicpc

#### - [1065](https://www.acmicpc.net/problem/1065) 한수
```
const readline = require('readline');
const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
})
let input;
let answer =99;
rl.on("line", function(line){
   input = parseInt(line);
   if(input>=100){
    for(let i =100;i<=input;i++){
        let a= parseInt(i/100);
        let b = parseInt((i/10)%10);
        let c = parseInt(i%10);
        if((a-b) == (b-c)){
            answer++;
        }
    }
    console.log(answer);
   }else{
       console.log(input);
   }
   rl.close()
}).on('close',function(){
})
```

#### - [2851](https://www.acmicpc.net/problem/2851) 슈퍼마리오
```
const readline = require('readline');
const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
})
let input;
let answer=0;
let close = false;
let temp=0;
let i =0;
rl.on("line", function(line){
    input = parseInt(line);
    if(!close){
        temp+=input;
        if(temp>100){
            if(temp-100<=100-answer){
                answer = temp;
            }
            close=true
        }else{
            answer = temp;
        }
    }
    i++
    if(i==10){
        rl.close()
    }
}).on('close',function(){
    console.log(answer);
})
```

#### - [11726](https://www.acmicpc.net/problem/11726) 2*n 타일링
```
const readline = require('readline');
const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
})
let n;
let arr= [1,2];
const dpFunc = ()=>{
    for(let i =2; i<1008;i++){
        arr[i]=parseInt((arr[i-1]+ arr[i-2])%10007)
    }
}

dpFunc()
rl.on("line", function(line){
    n = parseInt(line);
    rl.close()
}).on('close',function(){
    console.log(arr[n-1]);
})
```
#### - [10825](https://www.acmicpc.net/problem/10825) 국영수
```

```

#### - [2798](https://www.acmicpc.net/problem/2798) 블랙잭
``` 
const readline = require('readline');
const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
})
let input = [];
let n ;
let m ;
let i =0;
let answer = 0;
rl.on("line", function(line){
    input = line.split(' ').map((v)=>{return parseInt(v)});
    i++
    if( i==1){
        n = input[0];
        m = input[1];   
    }
    if(i==2){
        input.sort();
        for(let i =0; i<n-2 ; i++){
            for(let j =i+1; j<n-1 ;j++){
                for(let k= j+1; k<n; k++){
                    temp = input[i]+input[j]+input[k];
                    if(answer<temp &&temp<=m){
                        answer = temp
                    }
                }
            }
        }
        rl.close()
    }
}).on('close',function(){
    console.log(answer);
})
```

#### -[1018](https://www.acmicpc.net/problem/1018)체스판 다시칠하기
```
const readline = require('readline');
const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
})
let input = [];
let arr = [];
let row ;
let cell ;
let i =0;
let answer =10000;

const checkW = (row,cell)=>{
    let ans =0;
    for(let i =cell+1;i<cell+8;i+=2){
        if (arr[row][i] =='W')
            ans++;
    }
    return ans;
}

const checkB = (row, cell) => {
    let ans = 0;
    for (let i = cell + 1; i < cell + 8; i += 2) {
        if (arr[row][i] == 'B')
            ans++;
    }
    return ans;
}


rl.on("line", function(line){
    input = line.split(' ').map((v)=>{return parseInt(v)});
    if( i==0){
        row = input[0];
        cell = input[1];   
    }else {
        arr.push(line.split(''))
        if (i == row) {
            for(let i =0;i<row-7;i++){
                for(let j =0;j<cell-7;j++){

                    let chk = 0;
                    //let first block has to black
                    let temp = 0;
                    let dummy_row = i;
                    
                    for(let k = 0; k<8;k++){
                        if(chk%2==0){
                            temp+=checkW(dummy_row+k,j-1);
                            temp += checkB(dummy_row + k, j);
                        }else{
                            temp += checkW(dummy_row + k, j);
                            temp += checkB(dummy_row + k, j - 1);
                        }
                        chk++;
                    }
                    if(temp<answer){
                        answer = temp
                    }
                    
                    //let first block has to white
                    temp=0;
                    chk=0;
                    for (let k = 0; k < 8; k++) {
                        if (chk % 2 == 0) {
                            temp += checkW(dummy_row + k, j);
                            temp += checkB(dummy_row + k, j-1);
                        } else {
                            temp += checkW(dummy_row + k, j-1);
                            temp += checkB(dummy_row + k, j);
                        }
                        chk++;
                    }
                    if (temp < answer) {
                        answer = temp
                    }
                }
            }
            rl.close()
        }
    }
    i++;
}).on('close',function(){
    console.log(answer);
})
```

#### -[9461](https://www.acmicpc.net/problem/9461) 파도반 수열
```
const readline = require('readline');
const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
})
let arr = [1,1,1]
const func = ()=>{
    for (let i =3;i<103;i++){
        arr[i]=arr[i-2]+arr[i-3];
    }
}
func();

let input = []
let chk = 0;
let T =0;
rl.on("line", function(line){
   input = parseInt(line);
   if(chk==0){
        T=input;
   }else{
        input =parseInt(line);
        console.log(arr[input-1]);
        if(chk==T){
            rl.close();
        }
    }
    chk++;
}).on('close',function(){
})

```