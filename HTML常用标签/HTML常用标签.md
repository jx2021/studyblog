[TOC]



# HTML常用标签

## 1. a标签的用法

*  href (hyper reference)

* target 

  利用同一个页面打开不同的窗口

  ```html
  <a href="//baidu.com" target="xxx">baidu</a>
  <a href="//taobao.com" target="xxx">taobao</a>
  ```

  

* download

* rel=noopener

  ```html
  <a href="http://google.com" target="_blank" download>跳转到google(打开新页面)</a>
  <a href="http://google.com" target="_self" download>在当前页面打开</a>
  <a href="http://google.com" target="_top" download>在最上面一层打开</a>
  <a href="http://google.com" target="_parent" download>在当前页面的上一层打开</a>
  <a href="javascript:alert(1);">javascript伪协议</a>
  <a href="javascript:;">点击没有任何反应</a>
  <a href="#xxx">跳转到指定标签</a>
  <a href="mailto: xxxxx@gmail.com">发邮件</a>
  <a href="tel: 1300000000">打电话给我</a>
  
  ```

  

## 2. img标签的用法

* #### 作用

  发出get请求展示一张图片

* #### 属性

  ```html
  <img width="100" height="500"  src="picture.png" alt="图片">
  ```

* #### 事件

  onload/onerror

* #### 响应式

  max-width: 100%

## 3. table标签的用法

### 相关标签

* thead

* tbody

* tfoot

  ```html
      <table>
          <thead>
              <tr>
                  <th></th>
                  <th>hong</th>
                  <th>ming</th>
                  <th>ying</th>
              </tr>
          </thead>
          <tbody>
              <tr>
                  <th>shu</th>
                  <td>61</td>
                  <td>91</td>
                  <td>85</td>
              </tr>
              <tr>
                  <th>yu</th>
                  <td>79</td>
                  <td>82</td>
                  <td>92</td>
              </tr>
              <tr>
                  <th>ying</th>
                  <td>100</td>
                  <td>97</td>
                  <td>87</td>
              </tr>
          </tbody>
          <tfoot>
              <tr>
                  <th>sum</th>
                  <td>200</td>
                  <td>200</td>                
                  <td>200</td>
              </tr>
          </tfoot>
      </table>
  ```

  

 ### 相关样式

 * table-layout

    ```html
    table{
    	table-layout: auto;
        border-collapse: collapse;
        border-spacing: 0;
    }
    table{
    	table-layout: fixed;
    }
    ```

    auto 根据内容判断宽度

    fixed 等宽

 * border-collapse 

 * border-spacing

## 4. form标签

* #### 作用

  发出get或post请求，然后刷新页面

* #### 属性

  action/ autocomplete/ method/ target

* #### 事件

  onsubmit

  button标签内还可以添加标签，input标签内只能有纯文本

  form里面的input要有name

  form里要放一个type=submit才能触发submit事件

```html
<form action="/xxx" method="POST" autocomplete="off" target="_blank">
    <input name="username" type="text" required>
    <input type="submit" value="提交">
    <button>提交2</button>
    <hr>
    <input type="password">
    <hr>
    <input type="color">
    <hr>
    <input name="gender" type="radio">male单元框
    <hr>
    <input name="gender"type="radio">female
    <hr>
    <input type="checkbox">多选框
    <hr>
    <input type="file" multiple>
    <hr>
    <input type="hidden">hidden
    <hr>
    <textarea name="" id="" cols="30" rows="10"></textarea>
    <hr>
    <textarea style="resize: none; width: 50%; height: 300px"></textarea>
    <hr>
    <select>
        <option value="">--请选择--</option>
        <option value="1">周一</option>
        <option value="2">周二</option>
        <option value="3">周三</option>
    </select>
</form>
```



