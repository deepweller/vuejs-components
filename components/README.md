# Date picker

## Options

* 기간설정 옵션 (선택안할 시 **default로 0**만 선택)
	* 0: 오늘
	* 1: 지난주
	* 2: 지난달
	* 3: 지난3달 
	* 4: 지난1년 

## Usage

```html
<template>
    <div>
        <!-- 옵션설정 안하는 경우 -->
        <DatePicker v-on:datePick="changeDatePicker" ref="commonDatePicker">발송일</DatePicker>
        <!-- 옵션설정 하는 경우 -->
        <DatePicker v-on:datePick="changeDatePicker" ref="commonDatePicker" v-bind:optionsProps="[0, 2, 4]">발송일</DatePicker>
    </div>
</template>

<script>
export default {
    data() {
        return {
            searchStartDt: '',
            searchEndDt: '',
        }
    },
    methods: {      
        changeDatePicker(value) {
            this.searchStartDt = value[0];
            this.searchEndDt = value[1];
        },
        resetDatePicker() {
            this.$refs.commonDatePicker.setNowDt();
        },
    }
}
</script>
```