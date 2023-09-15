## datepicker 
> [참고자료](https://blog.naver.com/PostView.naver?blogId=varkiry05&logNo=222521615050)
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/226883e3-e405-4241-b9d5-a6c23a88be1e)



```js
import LocalizationProvider from '@mui/lab/LocalizationProvider';
import AdapterDateFns from '@mui/lab/AdapterDateFns';
import DesktopDatePicker from '@mui/lab/DesktopDatePicker';
...

const [startDate, setStartDate] = useState()
...
	<LocalizationProvider dateAdapter={AdapterDateFns}>
	  <DesktopDatePicker
	      label={"수강기간 (From)"}
	      value={startDate}
          inputFormat={"yyyy-MM-dd"}
          mask={"____-__-__"}
	      onChange={(newValue) => {
            setStartDate(newValue)
	      }}
	      renderInput={(params) => <TextField {...params} />}
	  />
	</LocalizationProvider>
...
```
