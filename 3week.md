## 1. javascript acmicpc

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
