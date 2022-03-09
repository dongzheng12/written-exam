# 笔试题  

请完成以下笔试题，可以使用自己擅长的语言来编写，通过 github pull request 提交代码。

1. 编写一个递归版本的 reverse(s) 函数(或方法),以将字符串s倒置。
  function reverse(arr,len,a){
    if(len>=1){  
      
       let temp = arr.shift();   
       
       a[len-1] = temp;
       
       len=len-1;
       reverse(arr,len,a);
    }
    return a;
}
function handleRes(s){
    let arr = s.split('');
    let len = arr.length;
    let a = [];
    let answer = reverse(arr,len,a).join('');
    return answer;
}

2. 编写程序 expr，以计算从命令行输入的逆波兰表达式的值，其中每个运算符或操作数用一个单独的参数表示。例如，命令
expr 2 3 4 + *
var evalRPN = function(tokens) {
    let tmp = [],
        a = 0,
        b = 0;
    for(let i = 0; i < tokens.length; i++){
        if(tokens[i] == '+'){
            a = parseInt(tmp.pop());
            b = parseInt(tmp.pop());
            tmp.push(a + b);
        }else if(tokens[i] == '-'){
            a = parseInt(tmp.pop());
            b = parseInt(tmp.pop());
            tmp.push(b - a);
        }else if(tokens[i] == '*'){
            a = parseInt(tmp.pop());
            b = parseInt(tmp.pop());
            tmp.push(a * b);
        }else if(tokens[i] == '/'){
            a = parseInt(tmp.pop());
            b = parseInt(tmp.pop());
            tmp.push(parseInt(b / a));
        }else{
            tmp.push(tokens[i]);
        }
    }
    return tmp[0];
};

3. 用归并排序将3，1，4，1，5，9，2，6 排序。
function mergeSort(arr) { 

var len = arr.length;

if (len < 2) {

    return arr;

}

var middle = Math.floor(len / 2),

    left = arr.slice(0, middle),

    right = arr.slice(middle);

return merge(mergeSort(left), mergeSort(right));

}



function merge(left, right) {

var result = [];



while (left.length>0 && right.length>0) {

    if (left[0] <= right[0]) {

        result.push(left.shift());

    }else {

        result.push(right.shift());

    }

}



while (left.length)

    result.push(left.shift());



while (right.length)

    result.push(right.shift());



return result;

}

4. 对下面的 json 字符串 serial 相同的进行去重。

let arr = [{
    "name": "张三",
    "serial": "0001"
  }, {
    "name": "李四",
    "serial": "0002"
  }, {
    "name": "王五",
    "serial": "0003"
  }, {
    "name": "王五2",
    "serial": "0003"
  }, {
    "name": "赵四",
    "serial": "0004"
  }, {
    "name": "小明",
    "serial": "005"
  }, {
    "name": "小张",
    "serial": "006"
  }, {
    "name": "小李",
    "serial": "006"
  }, {
    "name": "小李2",
    "serial": "006"
  }, {
    "name": "赵四2",
    "serial": "0004"
  }];
  function unique2(arr) {
            var obj = [];
            for (var i = 0; i < arr.length; i++) {
                var ele = arr[i];
                
                if(!obj.some(function(age){
                    
                    return age.serial==ele.serial
                })){
                   obj.push(ele)
                 
                }
            }
        return obj
            
        }
       
        unique2(arr)
```javascript
  [{
    "name": "张三",
    "serial": "0001"
  }, {
    "name": "李四",
    "serial": "0002"
  }, {
    "name": "王五",
    "serial": "0003"
  }, {
    "name": "王五2",
    "serial": "0003"
  }, {
    "name": "赵四",
    "serial": "0004"
  }, {
    "name": "小明",
    "serial": "005"
  }, {
    "name": "小张",
    "serial": "006"
  }, {
    "name": "小李",
    "serial": "006"
  }, {
    "name": "小李2",
    "serial": "006"
  }, {
    "name": "赵四2",
    "serial": "0004"
  }];
```

5. 把下面给出的扁平化json数据用递归的方式改写成组织树的形式
function arrayToJson(treeArray){
  var r = [];
  var tmpMap ={};
 
  for (var i=0 ;i<treeArray.length; i++) {
   tmpMap[treeArray[i]["id"]]= treeArray[i]; 
  } 
  for (i=0, l=treeArray.length; i<l; i++) {
   var key=tmpMap[treeArray[i]["pid"]];
   if (key) {
    if (!key["children"]){
      key["children"] = [];
      key["children"].push(treeArray[i]);
    }else{
     key["children"].push(treeArray[i]);
    }    
   } else {
    r.push(treeArray[i]);
   }
  }
  return r
  }

```javascript
  [
    {
      "id": "1",
      "name": "中国",
      "code": "110",
      "parent": ""
    },
    {
      "id": "2",
      "name": "北京市",
      "code": "110000",
      "parent": "110"
    },
    {
      "id": "3",
      "name": "河北省",
      "code": "130000",
      "parent": "110"
    },
    {
      "id": "4",
      "name": "四川省",
      "code": "510000",
      "parent": "110"
    },
    {
      "id": "5",
      "name": "石家庄市",
      "code": "130001",
      "parent": "130000"
    },
    {
      "id": "6",
      "name": "唐山市",
      "code": "130002",
      "parent": "130000"
    },
    {
      "id": "7",
      "name": "邢台市",
      "code": "130003",
      "parent": "130000"
    },
    {
      "id": "8",
      "name": "成都市",
      "code": "510001",
      "parent": "510000"
    },
    {
      "id": "9",
      "name": "简阳市",
      "code": "510002",
      "parent": "510000"
    },
    {
      "id": "10",
      "name": "武侯区",
      "code": "51000101",
      "parent": "510001"
    },
    {
      "id": "11",
      "name": "金牛区",
      "code": "51000102",
      "parent": "510001"
    }
  ];
```
