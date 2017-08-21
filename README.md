# 插入排序

### `思想:`

将一个记录（数）插入到已经拍好序的有序序列中，该数与已排好序的序列的每个记录（数）进行比较后放在合适的位置，从而得到一个新，记录数加1的有序列序列。

### `js实现`

```javascript
function insertSort(a){
	var len  = a.length;
	for (var i = 1; i < len; i++) {
		 var key = a[i],
		 j = i - 1;
		 while(j >= 0 ){
		 	if (a[j]  > key) {
		 		a[j + 1]  = a[j];
		 	}else{
		 		break;
		 	}
		 	j--;
		 }
		 a[j + 1] = key;
	}

	return a
}

//测试
var a = [5,9,8,10,3,7,13,12,2,20,4];

insertSort(a);
//[2, 3, 4, 5, 7, 8, 9, 10, 12, 13, 20]
```



# 希尔排序

### `思想：`

将整个待排序的记录序列分割成若干个子序列分别进行插入排序，待整个序列基本有序时再对全体的记录进行一次插入排序。

`子序列:` 

子序列的构成不是简单的”逐段分割“，而是将相隔某个“增量”的记录组成一个子序列。这样的好处是较小的不是一步一步的往前挪，而是跳跃式的往前移动。

### `js实现：`

```javascript
function sellSort(a){
  var len  = a.length,
  grap = Math.floor(len/2);
  while(grap > 0){
  console.log(grap)
    for(var k = 0;k<grap;k++){
      for(var i = k + grap;i <len;i = i + grap){
        var key = a[i],j;
        for(j = i - grap ;j >= 0;j = j - grap){
        	console.log("3");
          if(a[j] > key){
            a[j + grap]  = a[j];
          }else{
            break;
          }
        }
        a[j + grap] = key;
      }
    }
    grap =  Math.floor(grap/2);
  }
  return a;
}
//测试
var a = [5,9,8,10,3,7,13,12,2,20,4];
sellSort(a)
// [2, 3, 4, 5, 7, 8, 9, 10, 12, 13, 20]
```





# 冒泡排序

### `思想：`

将第一个记录与第二个记录进行比较，若为逆序，则将这两个记录交换。然后比较第二个与第三个记录。依次类推。直到最后一个记录与倒数第二个记录比较为止。


### `js实现：`

```javascript
function  bulle(a){
  var len  = a.length;
  //限制
  for(var i = len - 1;i > 0; i--){
    for(var j = 1; j <= i ; j++){
      //判断是否交换
      if(a[j - 1] > a[j]){
          var  temp = a[j];
          a[j] = a[j - 1];
          a[j - 1] = temp;
      }
    }
  }
  return a;
}

//测试
var a = [5,9,8,10,3,7,13,12,2,20,4];
bulle(a)
```



# 快速排序

### `思想：`

将待排序序列的记录分割成独立的两部分，其中一部分记录均比另一部分记录小。分别对这两部分数据进行排序（可递归）以达到整个有序序列有序。

### `js实现：`

```javascript
function quickSort(arr) {
　　if (arr.length <= 1) {
    	return arr; 
    }
　　var baseIndex = Math.floor(arr.length / 2);
　　var base = arr.splice(baseIndex, 1)[0];
　　var small = [];
　　var biggle = [];
　　for (var i = 0; i < arr.length; i++){
　　　　if (arr[i] < base) {
　　　　　　small.push(arr[i]);
　　　　} else {
　　　　　　biggle.push(arr[i]);
　　　　}
　　}
　　return quickSort(small).concat([base], quickSort(biggle));
};
```



# 选择排序

### `思想：`

每一趟循环都找出最大数或者最小数

### `js实现：`

```javascript
var a = [5,9,8,10,3,7,13,12,2,20,4];
function selectSort(a){
  var len  = a.length;
  for(var i = 0;i < a.length;i++){
    var min = a[i],index = i;
    for(var j = i + 1;j < a.length; j++){
      if(a[j] < min){
        min = a[j];
        index = j;
      }
    }
    if(index !== i){
      var temp = a[i];
      a[i] = min;
      a[index]  = temp;
    }

  }
    return a;
}
//测试
var a = [5,9,8,10,3,7,13,12,2,20,4];
selectSort(a)
```



# 归并排序

# 堆排序

# 基数排序






