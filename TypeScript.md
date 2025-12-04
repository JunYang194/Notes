# TypeScript 配置

```bash
# 生成配置文件tsconfig.json
tsc --init
```

# 类型

```tsx
number   > 任意数字
string   > 任意字符串
boolean  > 布尔值
字面量    > 限制变量的值就是该字面量的值
any      > 任意类型
unknown  > 类型安全的any
void     > 没有值(或undefined)
never    > 不能是任何值
object   > 任意JS对象
array    > 任意JS数组
tuple    > 元素，TS新增类型，固定长度数组
enum     > 枚举，TS新增类型
```

# 类型

```tsx
# 类型断言
变量 as 类型
<类型>变量

# 类型声明
let 变量: 类型 = 值  > 变量类型声明

let arr: 类型[]  > 数组类型声明
  
let obj: {
  [propName: 类型]: 类型  > 属性类型声明
  (a: 类型, b: 类型)=>类型  > 函数类型声明
}

type myType = {}

enum sex{girl:0 ,man: 1}  > 枚举

function fn(变量: 类型, 变量: 类型): 类型{  > 参数类型声明以及返回值类型声明
  ...
}
  
# 接口
interface 接口名{
  readonly 属性: 类型  > 只读属性
  属性?: 类型          > 可有可无属性
  name: string  接口属性(只能定义类型，不能有实际值)
  fn(): void    接口方法(只能定义类型，不能有实际值)
}

interface 接口名 extends 接口, ...{}  > 继承接口
 
# 实现接口
const 变量: 接口名 = function (属性: 类型): 类型{}
class 类名 implements 接口名{}
```

# class

```tsx
class 类名{
  # 修饰符
  public name: string     > 共有属性，任意位置可以访问(默认值)
  private name: string    > 私有属性，只能在当前类的内部访问，外部需要通过get/set方法来访问
  protected name: string  > 保护属性，只能在当前类/子类的内部访问
  readonly name: string   > 只读属性，只能在当前类的构造函数中修改，其他地方无法修改
  static name: string     > 静态属性，只能(父类.属性/方法)去访问，不能通过(this.属性/方法)去访问	
  
  # 构造函数
  constructor(public name: string='默认值'){  > 构造函数的参数一旦有了修饰符，当前类就不需要声明参数的类型
  	this._name = name
  }
  
  # 读取器
  get name(){               > 获取数据时自动进入该函数中
    return this._name
  }
        
  # 设置器
  set name(value: string){  > 设置数据时自动进入该函数中
    this._name = value
  }
}

# 抽象类
abstract class 父类{  抽象类，专门用来继承的类，不能创建子对象
  abstract name: string 抽象属性必须在子类重写
  abstract fn():void  抽象方法只能定义在抽象类中，子类必须对抽象方法重写
}
               
class 子类 extends 父类{
  super.prop  > 父类属性
	super(prop) > 父类属性
  super.fn()  > 父类方法
  super()     > 父类构造函数
  fn()        > 抽象类重写
}
```

# 函数

```tsx
const 变量: (参数: 类型) => 返回值的类型 = function (参数: 类型): 返回值的类型{
  return 参数
}
```

# 参数

```tsx
function(name: string='')  > 默认参数
function(name?: string)  > 可选参数
function(...arr: string[])  > 剩余参数
```

# 泛型

```tsx
# 定义函数类时，如果遇到类型不明确可以使用泛型
function fn<T>(a: T): T{}
class className<T>{}
fn<string>(a: 'hello')             > 指定泛型
new className<string>(a: 'hello')  > 指定泛型

# T extends Inter 指定泛型T必须是Inter的子类
interface Inter{
  length: number
}

function fn<T extends Inter>(a: T): number{
	return a.length
}
```

