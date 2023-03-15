## 함수 종료 방법
> [참고자료](https://minggu92.tistory.com/64)
- `return false` >>> ✔ break 와 같은 역할 수행


```javascript
function save($targetRows){
    let targetArr = [];
    
    for (let i = 0; i < $targetRows.length; i++) {
        const $targetRow = $($targetRows[i]);
        if (!sampleValid($targetRow)) 
        	return; //타겟 유효성검사
        let targetJson = {};
        targetJson.targetName = $targetRow.find('input[name="target_name"]').val();
        targetJson.targetBirthYear = $targetRow.find('select[name="birth_year"] option:selected').val();
        targetJson.targetGrade = $targetRow.find('input[type="radio"][name="grade"]:checked').val();
        targetJson.targetschoolNo = $targetRow.find('input[name="school_no"]').val();       
        targetArr.push(targetJson);
    }
    
    return targetArr;
}

function sampleValid($thisRow){
    $thisRow.find('dl[data-col="require"] input[type="text"]').each(function (idx, el) {
        const $el = $(el);
        if (fn_isEmpty($el.val() + $el.text())) {
            const $label = $('label[for="' + $el.attr('id') + '"').text();
            showError($el, $label + ' 항목을 입력해주세요.'); //input 밑에 error text 생성            
            $el.focus(); //빈 input태그로 포커스
            return false;
        } else
            hideError($el); //생성되어있는 error text hide
    });

    let saveBtn = $('#btnSave');
    if (saveBtn.is(":disabled")) saveBtn.prop('disabled', false); //버튼 중복클릭 방지
    return true;
    
    
    
function sampleValid($thisRow){
    try {
        $thisRow.find('dl[data-col="require"] input[type="text"]').each(function (idx, el) {
            const $el = $(el);
            if (fn_isEmpty($el.val() + $el.text())) {
                const $label = $('label[for="' + $el.attr('id') + '"').text();
                showError($el, $label + ' 항목을 입력해주세요.'); //input 밑에 error text 생성            
                $el.focus(); //빈 input태그로 포커스
                throw 'finish';
            } else
                hideError($el); //생성되어있는 error text hide
        });
    } catch(Exception){
        if (Exception !== 'finish') throw Exception;
        else return false;    	
    }
    
    let saveBtn = $('#btnSave');
    if (saveBtn.is(":disabled")) saveBtn.prop('disabled', false); //버튼 중복클릭 방지
    return true;
}
```
