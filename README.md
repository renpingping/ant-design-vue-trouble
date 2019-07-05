# ant-design-vue-trouble
ant design vue 踩坑记录

## ant 日期选择框 语言换为中文

第一步：根据官方文档导入下面的代码（放在使用日期选择框的界面也可以放在`main.js`里面）
 ```javascript
 import moment from 'moment';
 import 'moment/locale/zh-cn';
 moment.locale('zh-cn');
 ```
 引入之后确定按钮、选择按钮还是英文显示
 
 第二步：对上一步进行一个改善
 
 2-1：在你使用日期选择器的页面加入下面的这个变量（变量名随意，我就叫 `locale`）
 ```javascript
 export default {
  data() {
    return {
      locale:{          
        "lang": {            
          "placeholder": "请选择日期",            
          "today": "今天",            
          "yearFormat": "YYYY",            
          "dateFormat": "M/D/YYYY",            
          "dayFormat": "D",            
          "dateTimeFormat": "M/D/YYYY HH:mm:ss",            
          "monthFormat": "MMMM"       
          }
        },
      ...
      }
    }
  }
          
 ```
 2-2：在你的日期选择框上加上这句代码 `:locale=locale`
 ```javascript
 <a-date-picker 
    showTime
    time='time'
    format="YYYY-MM-DD HH:mm:ss"
    placeholder="请选择时间"
    :locale=locale
    v-decorator="[
        'time',
        {rules: [{ required: false, message: '请选择时间' }]}
    ]"
  />
 ```
 
 **日期选择器更多的配置**
 
  ```javascript
   locale:{       
     "lang": {         
      "placeholder": "请选择日期",          
      "rangePlaceholder": ["Start date", "End date"],         
      "today": "今天",          
      "now": "Now",         
      "backToToday": "Back to today",          
      "ok": "Ok",          
      "clear": "Clear",          
      "month": "Month",          
      "year": "Year",          
      "timeSelect": "Select time",          
      "dateSelect": "Select date",          
      "monthSelect": "Choose a month",          
      "yearSelect": "Choose a year",          
      "decadeSelect": "Choose a decade",          
      "yearFormat": "YYYY",          
      "dateFormat": "M/D/YYYY",          
      "dayFormat": "D",          
      "dateTimeFormat": "M/D/YYYY HH:mm:ss",          
      "monthFormat": "MMMM",          
      "monthBeforeYear": true,          
      "previousMonth": "Previous month (PageUp)",          
      "nextMonth": "Next month (PageDown)",          
      "previousYear": "Last year (Control + left)",          
      "nextYear": "Next year (Control + right)",          
      "previousDecade": "Last decade",          
      "nextDecade": "Next decade",          
      "previousCentury": "Last century",          
      "nextCentury": "Next century"        
      },        
      "timePickerLocale": {          
        "placeholder": "Select time"        
      }      
    }
  ```
 
