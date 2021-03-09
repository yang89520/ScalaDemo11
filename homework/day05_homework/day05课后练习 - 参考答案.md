# day05课后练习
{: id="20210309203838-i8prjzc"}

# 一维数组基础题目
{: id="20210309203838-adjv1mc"}

## 第一题：需求实现
{: id="20210309203838-24zue1f"}

* {: id="20210309203838-o2wqt55"}模拟大乐透号码：
  {: id="20210309203838-k6bumeu"}

  * {: id="20210309203838-neplfjs"}一组大乐透号码由10个1-99之间的数字组成
    {: id="20210309203838-4x39cqm"}
  * {: id="20210309203838-jd8ec4r"}打印大乐透号码信息
    {: id="20210309203838-lbkkckw"}
  {: id="20210309203838-d8kqaj0"}
* {: id="20210309203838-ityu8wn"}代码实现，效果如图所示：
  {: id="20210309203838-68axojg"}
  ![](img\1.jpg)
  {: id="20210309203838-8qslc3k"}
* {: id="20210309203838-kmws1hg"}开发提示：
  {: id="20210309203838-xu4ve3t"}
  * {: id="20210309203838-3hvvbro"}使用数组保存录入或随机产生的号码
    {: id="20210309203838-xi07ynk"}
  * {: id="20210309203838-utjb8gl"}如果使用键盘输入，需要用到java.util.Scanner
    {: id="20210309203838-sqe6cpe"}
  * {: id="20210309203838-jyqrzp4"}如果使用随机产生，可以使用Math.random()或java.util.Random的nextInt(bounds)
    {: id="20210309203838-06g4f9g"}
  {: id="20210309203838-h48rlfg"}
{: id="20210309203838-71i3evo"}

```java
public class Test01 {

	public static void main(String[] args) {
		//1、声明并创建数组
		int[] arr = new int[10];
		
		//2、为元素赋值
		java.util.Random rand = new java.util.Random();
		for (int i = 0; i < arr.length; i++) {
			arr[i] = rand.nextInt(99)+1;
		}
		
		//3、输出
		for (int i = 0; i < arr.length; i++) {
			System.out.print(arr[i]+" ");
		}
	}

}
```
{: id="20210309203838-dy5join"}

## 第二题：需求实现
{: id="20210309203838-3gnc4ly"}

* {: id="20210309203838-v568huk"}打印扑克牌.
  {: id="20210309203838-21jpruq"}
* {: id="20210309203838-jqcundb"}代码实现，效果如图所示：
  {: id="20210309203838-gu09gf0"}
  ![](img\2.jpg)
  {: id="20210309203838-i3d7r8x"}
* {: id="20210309203838-c8ovsa9"}开发提示：
  {: id="20210309203838-683el40"}
  * {: id="20210309203838-6revyw4"}使用两个字符串数组，分别保存花色和点数
    {: id="20210309203838-xj8lere"}
  * {: id="20210309203838-9p7lary"}再用一个字符串数组保存最后的扑克牌
    {: id="20210309203838-w5v4xlo"}
  * {: id="20210309203838-4wsm2kg"}遍历显示
    {: id="20210309203838-xo6kfuj"}
  {: id="20210309203838-o6dm5iz"}
{: id="20210309203838-7hn9wyo"}

```java
public class Test02 {
	public static void main(String[] args){
		String[] hua = {"黑桃","红桃","梅花","方片"};
		String[] dian = {"A","2","3","4","5","6","7","8","9","10","J","Q","K"};
		String[] pu = new String[hua.length*dian.length];
		for(int i=0,k=0; i<hua.length; i++){
			for(int j=0; j<dian.length; j++,k++){
				pu[k] = hua[i]+dian[j];
			}
		}
		
		for (int i = 1; i <= pu.length; i++) {
			System.out.print(pu[i-1]+" ");
			if(i%13==0){
				System.out.println();
			}
		}
	}
}
```
{: id="20210309203838-kkw2ipg"}

## 第三题：需求实现
{: id="20210309203838-ma6l3f6"}

* {: id="20210309203838-nwfymui"}模拟在一副牌中，抽取第1张，第5张，第50张扑克牌。
  {: id="20210309203838-4pmv2ho"}
* {: id="20210309203838-cmelh7r"}代码实现，效果如图所示：
  {: id="20210309203838-hddkfop"}
  ![](img\3.jpg)
  {: id="20210309203838-ptcr9ti"}
{: id="20210309203838-fsol8xq"}

```
public class Test03 {
	public static void main(String[] args){
		String[] hua = {"黑桃","红桃","梅花","方片"};
		String[] dian = {"A","2","3","4","5","6","7","8","9","10","J","Q","K"};
		String[] pu = new String[hua.length*dian.length];
		for(int i=0,k=0; i<hua.length; i++){
			for(int j=0; j<dian.length; j++,k++){
				pu[k] = hua[i]+dian[j];
			}
		}
		
		System.out.println(pu[1-1] + " " + pu[5-1] +" " + pu[50-1]);
	}
}

```
{: id="20210309203838-gh0kx2t"}

## 第四题：需求实现
{: id="20210309203838-v0oglv0"}

* {: id="20210309203838-06v9sn0"}统计字符
  {: id="20210309203838-jn1ndvr"}

  * {: id="20210309203838-ylai3c4"}字符数组：{'a','l','f','m','f','o','b','b','s','n'}
    {: id="20210309203838-ya5gpiw"}
  * {: id="20210309203838-kjnbjqv"}统计每个字符出现的次数并打印到控制台。
    {: id="20210309203838-43dg2ha"}
  {: id="20210309203838-tam2bqm"}
* {: id="20210309203838-fl5fh92"}代码实现，部分效果如图所示：
  {: id="20210309203838-3dir815"}
  ![](img\4.jpg)
  {: id="20210309203838-f4r8ia4"}
* {: id="20210309203838-zrvwi73"}开发提示：
  {: id="20210309203838-jcsc9c5"}
  * {: id="20210309203838-5i73lu6"}将数字强制转换，根据ASCII码表转换为字符。
    {: id="20210309203838-hzmfztw"}
  * {: id="20210309203838-owcaut2"}可以定义长度26的数组，每个元素，对应去保存每种字符的出现次数，比如0索引保存a的次数，1索引保存b的次数，以此类推。
    {: id="20210309203838-gp49iqc"}
  {: id="20210309203838-0i80z7d"}
{: id="20210309203838-0fra14b"}

```java
public class Test04 {
	public static void main(String[] args){
		char[] arr = {'a','l','f','m','f','o','b','b','s','n'};
		
		int[] counts = new int[26];//counts数组的元素，目前默认值都是0
		/*
		counts[0] 存储 'a'字母出现的次数
		counts[1] 存储 'b'字母出现的次数
		counts[2] 存储 'c'字母出现的次数
		...
		*/
		//遍历arr数组，统计每一个字母出现的次数，并且把次数存储的counts数组中
		for(int i=0; i<arr.length; i++){
			//例如：arr[0]现在是'a'，那么应该counts[0]++
			//arr[1]现在是'l'，那么应该counts[11]++
			//找counts[下标]其中的下标与字母'a','b'等的关系
			//例如：'a' ==》counts[0]的[0]的关系		'a'-97=97-97=0
			//例如：'l' ==》counts[11]的[11]的关系		'l'-97=108-97=11
			counts[arr[i] - 97]++;
		}
		
		//遍历counts数组显示结果
		for(int i=0; i<counts.length; i++){
			if(counts[i]!=0){
				//System.out.println(字母 + "--" + 次数);
				System.out.println((char)(i+97) + "--" + counts[i]);
			}
		}
	}
}
```
{: id="20210309203838-px12jwy"}

## 第五题：需求实现
{: id="20210309203838-hw704pu"}

* {: id="20210309203838-kjx7nbz"}统计高于平均分的分数有多少个。
  {: id="20210309203838-ygr1ld9"}

  * {: id="20210309203838-h5j0t92"}定义数组[95, 92, 75, 56, 98, 71, 80, 58, 91, 91]。
    {: id="20210309203838-eio93ac"}
  {: id="20210309203838-17icjib"}
* {: id="20210309203838-pc6o9br"}代码实现，效果如图所示：
  {: id="20210309203838-svwtjn2"}
  ![](img\5.jpg)
  {: id="20210309203838-82v41u1"}
  步骤：
  {: id="20210309203838-wyu71pt"}
  （1）先求总分
  {: id="20210309203838-z8syqo8"}
  （2）求平均分
  {: id="20210309203838-2so2pea"}
  （3）遍历数组，统计比平均分高的个数
  {: id="20210309203838-e6fzmfx"}
{: id="20210309203838-sujuyrc"}

```java
public class Test05 {
	public static void main(String[] args) {
		int[] arr = {95, 92, 75, 56, 98, 71, 80, 58, 91, 91};
		
		//累加总分
		int sum = 0;
		for (int i = 0; i < arr.length; i++) {
			sum += arr[i];
		}
		//求平均分
		int avg = sum/arr.length;
		
		//统计比平均分高的人数
		int count = 0;
		for (int i = 0; i < arr.length; i++) {
			if(arr[i] > avg){
				count++;
			}
		}
		System.out.println("高于平均分：" + avg + "的有" + count + "个");
	}
}
```
{: id="20210309203838-m7jg6h9"}

## 第六题：需求实现
{: id="20210309203838-80cuyr0"}

* {: id="20210309203838-9ba6b8y"}判断数组中的元素值是否对称.
  {: id="20210309203838-d8stoab"}
* {: id="20210309203838-egp18ww"}代码实现，效果如图所示：
  {: id="20210309203838-e3rkw6a"}
  ![](img\6.jpg)
  {: id="20210309203838-pbpydn8"}
* {: id="20210309203838-q7gjhoc"}开发提示：
  {: id="20210309203838-8kc3le1"}
  * {: id="20210309203838-o6on6wv"}数组中元素首尾比较。
    {: id="20210309203838-3f215rn"}
  {: id="20210309203838-vmlb1vk"}
{: id="20210309203838-4gcft6a"}

```java

public class Test06 {
	public static void main(String[] args){
		int[] arr = {1,2,3,4,4,3,2,1};
		
		//(1)先假设它是对称的
		boolean flag = true;
		
		//(2)遍历，查看数组的元素是否首尾对称
		//left表示左边的下标
		//right表示右边的下标
		for(int left=0,right=arr.length-1; left<right; left++,right--){
			if(arr[left] != arr[right]){
				flag = false;
				break;
			}
		}
		
		System.out.println(flag?"对称":"不对称");
	}
}

```
{: id="20210309203838-3xvh8ug"}

## 第七题：需求实现
{: id="20210309203838-mg62zs3"}

* {: id="20210309203838-251j1kk"}比较两个数组内容是否完全一致。
  {: id="20210309203838-go1io8v"}
* {: id="20210309203838-bjezakp"}代码实现，效果如图所示：
  {: id="20210309203838-o2tumso"}
  ![](img\7.jpg)
  {: id="20210309203838-q6nej1y"}
* {: id="20210309203838-xdl06fb"}开发提示：
  {: id="20210309203838-nviywi3"}
  * {: id="20210309203838-0u9mvkf"}长度一致，内容一致，定义为完全一致。
    {: id="20210309203838-4ksptmp"}
  {: id="20210309203838-r0fk7fx"}
{: id="20210309203838-r2tjqm7"}

```java
public class Test07 {
	public static void main(String[] args) {
		int[] arr1 = {1,2,3,4,5,6,7};
		int[] arr2 = {1,2,3,4,5,6,7};
	
		boolean flag = true;//假设一致
		if(arr1.length!=arr2.length){
			flag = false;
		}else{
			for (int i = 0; i < arr2.length; i++) {
				if(arr1[i] != arr2[i]){
					flag = false;
					break;
				}
			}
		}
		System.out.println("是否一致：" + flag);
	}
}

```
{: id="20210309203838-84134mj"}

## 第八题：需求实现
{: id="20210309203838-ufsuxge"}

- {: id="20210309203838-butpz9g"}根据标准答案【ADBCD】，每题2分共10分，求出每名学生最终得分。
  {: id="20210309203838-mrsgn84"}

  - {: id="20210309203838-6o68q9i"}四名同学答案分别为：
    {: id="20210309203838-iw98r89"}
    - {: id="20210309203838-6tgnsiw"}小尚：【DCBAD】
      {: id="20210309203838-yzqeekx"}
    - {: id="20210309203838-s7gajod"}小硅：【ADBCD】
      {: id="20210309203838-frit4we"}
    - {: id="20210309203838-04kq87l"}小谷：【ADBCA】
      {: id="20210309203838-altaf2u"}
    - {: id="20210309203838-yk12q7t"}小好：【ABCDD】
      {: id="20210309203838-fz06s42"}
    {: id="20210309203838-bm9lazr"}
  - {: id="20210309203838-3m87p1g"}每答对一题，得2分，输出四名同学的最终得分。
    {: id="20210309203838-c1cpcfr"}
  {: id="20210309203838-2jd2eut"}
- {: id="20210309203838-v0bxypz"}代码实现，效果如图所示：
  {: id="20210309203838-dehq3tc"}
  ![1557474285266](img/8.png)
  {: id="20210309203838-b99o2rm"}
  提示：标准答案放到一个一维数组中，每个同学答案也各自放到一个一维数组中，然后分别统计得分
  {: id="20210309203838-3i9h8oj"}
{: id="20210309203838-r9bto3x"}

```java
public class Test08 {
	public static void main(String[] args){
		//标准答案：
		char[] answer = {'A','D','B','C','D'};
		
		//学生的答案
		char[] shang = {'D','C','B','A','D'};
		char[] gui = {'A','D','B','C','D'};
		char[] gu = {'A','D','B','C','A'};
		char[] hao = {'A','B','C','D','D'};
		
		//求出每名学生最终得分。
		int shangFen = 0;
		for(int i=0; i<shang.length; i++){
			if(shang[i] == answer[i]){
				shangFen +=2;
			}
		}
		System.out.println("小尚的分数：" + shangFen);
		
		int guiFen = 0;
		for(int i=0; i<gui.length; i++){
			if(gui[i] == answer[i]){
				guiFen +=2;
			}
		}
		System.out.println("小硅的分数：" + guiFen);
		
		int guFen = 0;
		for(int i=0; i<gu.length; i++){
			if(gu[i] == answer[i]){
				guFen +=2;
			}
		}
		System.out.println("小谷的分数：" + guFen);
		
		int haoFen = 0;
		for(int i=0; i<hao.length; i++){
			if(hao[i] == answer[i]){
				haoFen +=2;
			}
		}
		System.out.println("小好的分数：" + haoFen);
	}
}
```
{: id="20210309203838-g5hveye"}

## 第九题：
{: id="20210309203838-9no91xz"}

案例：从键盘输入本组学员的人数，和本组学员的成绩，用数组存储成绩，然后实现从高到低排序
{: id="20210309203838-neaw70h"}

```java
public class Test01 {
	public static void main(String[] args){
		java.util.Scanner input = new java.util.Scanner(System.in);
		
		//(1)先确定人数，即确定数组的长度
		System.out.print("请输入本组学员的人数：");
		int count = input.nextInt();
		
		//(2)创建数组
		int[] scores = new int[count];
		
		//(3)输入学员的成绩
		for(int i=0; i<scores.length; i++){
			System.out.print("请输入第" +(i+1)+"个学员的成绩：");
			scores[i] = input.nextInt();
		}
		
		//(4)排序，冒泡
		for(int i=1; i<scores.length; i++){
			//从高到低，即从大到小
			//例如：5个人
			//从左到右，j的起点是0，
			//终点是3,2,1,0
			//arr[j] 与arr[j+1]
			for(int j=0; j<scores.length-i; j++){
				if(scores[j] < scores[j+1]){
					int temp = scores[j];
					scores[j] = scores[j+1];
					scores[j+1] = temp;
				}
			}
		}
		
		//(5)显示结果
		for(int i=0; i<scores.length; i++){
			System.out.print(scores[i]+ " ");
		}
	}
}

```
{: id="20210309203838-8nufjgp"}

## 第十题：
{: id="20210309203838-sjqccb8"}

案例：从键盘输入本组学员的人数，和本组学员的姓名，用数组存储姓名，然后再从键盘输入一个姓名，查找它是否在之前的数组中，如果存在，就显示它的下标
{: id="20210309203838-vtu9ted"}

```java
public class Test02 {
	public static void main(String[] args){
		java.util.Scanner input = new java.util.Scanner(System.in);
		
		//(1)先确定人数，即确定数组的长度
		System.out.print("请输入本组学员的人数：");
		int count = input.nextInt();
		
		//(2)创建数组
		String[] names = new String[count];
		
		//(3)输入学员的成绩
		for(int i=0; i<names.length; i++){
			System.out.print("请输入第" +(i+1)+"个学员的姓名：");
			names[i] = input.next();
		}
		
		//(4)输入要查找的学生姓名
		System.out.print("请输入要查找的学生姓名：");
		String name = input.next();
		
		//(5)查找
		int index = -1;
		for(int i=0; i<names.length; i++){
			if(name.equals(names[i])){
				index = i;
				break;
			}
		}
		if(index==-1){
			System.out.println(name+"不存在");
		}else{
			System.out.println(name +"在数组的下标是：" + index);
		}
	}
}
```
{: id="20210309203838-kj29wlt"}

## 第十一题：
{: id="20210309203838-31gnxzu"}

案例：从键盘输入一个英语单词，然后查找这个单词中是否存在'a'字母
{: id="20210309203838-jen1fui"}

提示：把字符串转成字符数组，可以使用String类型的toCharArray()方法
{: id="20210309203838-3lh7f87"}

```java
String str = "hello";
char[] arr = str.toCharArray();//arr数组中就是{'h','e','l','l','o'}
```
{: id="20210309203838-zzaf0xn"}

```java
public class Test03 {
	public static void main(String[] args) {
		java.util.Scanner input = new java.util.Scanner(System.in);
		
		System.out.print("请输入一个英语单词：");
		String word = input.next();
		
		char[] arr = word.toCharArray();
		int index = -1;
		for (int i = 0; i < arr.length; i++) {
			if(arr[i] == 'a'){
				index = i;
				break;
			}
		}
		if(index==-1){
			System.out.println(word+"中没有a");
		}else{
			System.out.println("a在"+word+"中的下标是：" + index);
		}
	}
}
```
{: id="20210309203838-bmvy06w"}

## 第十二题：
{: id="20210309203838-3t6ryon"}

随机验证码。
{: id="20210309203838-p4v3q87"}

* {: id="20210309203838-83hhcb1"}随机生成十组六位字符组成的验证码。
  {: id="20210309203838-dts1phg"}
* {: id="20210309203838-omw6gix"}验证码由大小写字母、数字字符组成。
  {: id="20210309203838-sft8qgc"}
{: id="20210309203838-xfop0zv"}

![1559037934272](img/1559037934272.png)
{: id="20210309203838-a0qitz6"}

开发提示：
{: id="20210309203838-ptccv2r"}

* {: id="20210309203838-ftskhr2"}使用字符数组保存原始字符，利用Random类生成随机索引。
  {: id="20210309203838-5y7vn3a"}
{: id="20210309203838-sv42cgy"}

```java
public class Test04 {
	public static void main(String[] args) {
		String[] arr = new String[10];
		java.util.Random rand = new java.util.Random();
		for (int i = 0; i < arr.length; i++) {
			arr[i] = "";
			for (int j = 0; j < 6; j++) {
				int num;
				while(true){
					num = rand.nextInt(123);
					//数字[48,57]  大写字母[65,90]  小写字母[97,122]
					if(num>=48 && num<=57){
						break;
					}else if(num>=65 && num<=90){
						break;
					}else if(num>=97 && num<=122){
						break;
					}
				}
				arr[i] += (char)num;
			}
		}
		
		for (int i = 0; i < arr.length; i++) {
			System.out.println("随机验证码：" + arr[i]);
		}
	}
}
```
{: id="20210309203838-95lpa6i"}

# 二维数组基础题目
{: id="20210309203838-nq05wqo"}

## 第1题：
{: id="20210309203838-6sh5ff5"}

* {: id="20210309203838-uft2rx7"}使用二维数组打印一个 10 行杨辉三角.
  {: id="20210309203838-o6qitqa"}

  1
  {: id="20210309203838-4v40ir1"}

  1 1
  {: id="20210309203838-p1daj3n"}

  1 2 1
  {: id="20210309203838-lgt2201"}

  1 3 3  1
  {: id="20210309203838-97chbag"}

  1 4 6  4  1
  {: id="20210309203838-qslm0qc"}

  1 5 10 10 5 1
  {: id="20210309203838-wfi9gaa"}

  ....
  {: id="20210309203838-mk2flgv"}
* {: id="20210309203838-s0kywnf"}开发提示
  {: id="20210309203838-3eur76a"}
{: id="20210309203838-lwa9h81"}

1. {: id="20210309203838-sfmo3sk"}第一行有 1 个元素, 第 n 行有 n 个元素
   {: id="20210309203838-v7lxc9a"}
2. {: id="20210309203838-hxkuh4g"}每一行的第一个元素和最后一个元素都是 1
   {: id="20210309203838-2vfiyy6"}
3. {: id="20210309203838-lfe7lw9"}从第三行开始, 对于非第一个元素和最后一个元素的元素.
   {: id="20210309203838-88x5dgp"}
   ```
   yanghui[i][j] = yanghui[i-1][j-1] + yanghui[i-1][j];
   ```
   {: id="20210309203838-2l8zjfs"}
   ![1558397196775](img/1558397196775.png)
   {: id="20210309203838-ev6shmk"}
{: id="20210309203838-alvuefw"}

```java
public class Test05 {
	public static void main(String[] args){
		//(1)先确定行数
		int[][] yanghui = new int[10][];
		
		//(2)再确定每一行的列数
		//第一行有 1 个元素, 第 n 行有 n 个元素
		for(int i=0; i<yanghui.length; i++){
			yanghui[i] = new int[i+1];
		}
		
		//(3)再确定元素
		for(int i=0; i<yanghui.length; i++){
			//每一行的第一个和最后一个元素都是1
			yanghui[i][0] = 1;
			yanghui[i][i] = 1;
			
			//中间的元素
			for(int j=1; j<yanghui[i].length-1; j++){
				yanghui[i][j] = yanghui[i-1][j-1] + yanghui[i-1][j];
			}
			
		}
		
		//(4)打印显示
		for(int i=0; i<yanghui.length; i++){
			for(int j=0; j<yanghui[i].length; j++){
				System.out.print(yanghui[i][j] + "\t");
			}
			System.out.println();
		}
	}
}
```
{: id="20210309203838-msd8oku"}

## 第2题：
{: id="20210309203838-hejcawk"}

* {: id="20210309203838-6rqeg82"}打印扑克牌，效果如图所示：
  {: id="20210309203838-qp1rc99"}

  ![](img/2.jpg)
  {: id="20210309203838-4uirci0"}
* {: id="20210309203838-7sh0smv"}开发提示：
  {: id="20210309203838-2adcws7"}
  * {: id="20210309203838-18o4oun"}使用一个两行的二维的字符串数组，分别保存花色和点数
    {: id="20210309203838-xeg1ick"}
  {: id="20210309203838-rk6cz33"}
{: id="20210309203838-0g4h83b"}

```java
public class Test06 {
	public static void main(String[] args){
		//1、声明一个二维数组，并确定长度
		String[][] arr = new String[2][];
		
		//2、确定第一行的列数，第一行存储花色
		arr[0] = new String[4];
		
		//3、确定第二行的列数，第二行存储点数
		arr[1] = new String[13];
		
		//4、把花色和点数放进去
		//花色
		arr[0][0] = "黑桃";
		arr[0][1] = "红桃";
		arr[0][2] = "梅花";
		arr[0][3] = "方片";
		
		//点数
		arr[1][0] = "A";
		for(int i=1; i<=9; i++){//表示第二行部分下标
			arr[1][i] = i+1+"";
		}
		arr[1][10] = "J";
		arr[1][11] = "Q";
		arr[1][12] = "K";
	
		//5、显示
		for(int i=0; i<arr[0].length; i++){//外循环循环花色
			for(int j=0; j<arr[1].length; j++){//内循环循环点数
				//arr[0][?]是花色
				//arr[1][?]是点数
				System.out.print(arr[0][i] + arr[1][j] + " ");
			}
			System.out.println();
		}
	}
}
```
{: id="20210309203838-6l7ln7z"}

## 第3题：
{: id="20210309203838-lahzrzb"}

需求：保存全班的每个组的成绩，并对成绩做统计
{: id="20210309203838-wz3uzca"}

1. {: id="20210309203838-vhd8jzp"}从键盘输入一共有几组
   {: id="20210309203838-3xb8qd3"}
2. {: id="20210309203838-0txow35"}从键盘输入每一组分别有多少人
   {: id="20210309203838-i5hbnbs"}
3. {: id="20210309203838-dj9dq6c"}从键盘输入每一个同学的成绩
   {: id="20210309203838-3g5ppw6"}
4. {: id="20210309203838-qekdbv4"}统计每一组的最高分、最低分
   {: id="20210309203838-vzx5gbj"}
5. {: id="20210309203838-2oqtxto"}统计每一组的平均分
   {: id="20210309203838-c6aftil"}
6. {: id="20210309203838-1utc7uf"}统计全班的最高分、最低分
   {: id="20210309203838-8srtc7l"}
7. {: id="20210309203838-gcfi115"}统计全班的平均分
   {: id="20210309203838-plqztbg"}
8. {: id="20210309203838-gprdnzh"}统计全班的总人数
   {: id="20210309203838-lnbol1l"}
{: id="20210309203838-1y36dhl"}

```java
public class Test07 {
	public static void main(String[] args){
		java.util.Scanner input = new java.util.Scanner(System.in);
		
		//(1)从键盘输入一共有几组，确定二维数组的行数
		System.out.print("请输入一共有几组：");
		int group = input.nextInt();
		
		//(2)创建二维数组，并确定行数
		int[][] arr = new int[group][];
		
		//(3)从键盘输入每一组分别有多少人，确定每一行的列数
		for(int i=0; i<arr.length; i++){
			System.out.print("请输入第" + (i+1) + "组有几个人:");
			arr[i] = new int[input.nextInt()];
			
			//(4)从键盘输入每一个同学的成绩
			for(int j = 0; j<arr[i].length; j++){
				System.out.print("请输入第" + (j+1) + "个组员的成绩：");
				arr[i][j] = input.nextInt();
			}
		}
		
		//(4)显示成绩表
		System.out.println("每组成绩如下：");
		for(int i=0; i<arr.length; i++){
			for(int j=0; j<arr[i].length; j++){
				System.out.print(arr[i][j] + "\t");
			}
			System.out.println();
		}
		
		/*
		4. 统计每一组的最高分、最低分
		5. 统计每一组的平均分
		6. 统计全班的最高分、最低分
		7. 统计全班的平均分
		8. 统计全班的总人数
		*/
		int[] groupMax = new int[group];//有几组就有几个元素
		int[] groupMin = new int[group];
		double[] groupAvg = new double[group];
		int max = -1;//全班的最高分
		int min = 101;//全班的最低分，假设成绩的范围是[0,100]
		double sum = 0;
		int count = 0 ;
		
		//把每一组的最高分，最低分，都初始化为特殊值
		for(int i=0; i<group; i++){
			groupMax[i] = -1;
			groupMin[i] = 101;
		}
		
		//统计
		for(int i=0; i<arr.length; i++){
			double groupSum = 0;//每一组累加总分，都是从0开始
			for(int j=0; j<arr[i].length; j++){
				if(arr[i][j] > groupMax[i]){//找每组的最高分
					groupMax[i] = arr[i][j];
				}
				if(arr[i][j] < groupMin[i]){//找每组的最低分
					groupMin[i] = arr[i][j];
				}
				if(arr[i][j] > max){//找全班的最高分
					max = arr[i][j];
				}
				if(arr[i][j] < min){//找全班的最低分
					min = arr[i][j];
				}
				groupSum += arr[i][j];//累加每一组的总分
				sum += arr[i][j];//累加全部的总分
				count++;//累加总人数
			}
			
			//每一组的平均分 = 每一组的总分/每一组的人数
			groupAvg[i] = groupSum / arr[i].length;
		}
		
		//全部的平均分 = 全部的总分 / 总人数
		double avg = sum / count;
		
		System.out.println("全班的最高分：" + max);
		System.out.println("全班的最低分：" + min);
		System.out.println("全班的平均分：" + avg);
		System.out.println("全班的总人数：" + count);
		for(int i=0; i<arr.length; i++){
			System.out.println("第" + (i+1) + "组的最高分：" + groupMax[i]);
			System.out.println("第" + (i+1) + "组的最低分：" + groupMin[i]);
			System.out.println("第" + (i+1) + "组的平均分：" + groupAvg[i]);
		}
	}
}
```
{: id="20210309203838-rexui8b"}


{: id="20210309203838-p2ugnon" type="doc"}
