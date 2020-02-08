# Date picker

기간의 범위를 설정할 수 있는 data picker, 리스트 검색필터에 사용

## Options

* Date picker label 설정

```html
<DatePicker>검색기간</DatePicker>
```

* 선택값 초기화

```html
<Button @click="resetDatePicker">Reset</Button>
```

* 기간설정 옵션 : `v-bind:optionsProps="[0, 1, 2]"`
	* 0: 오늘 (default)
	* 1: 지난주
	* 2: 지난달
	* 3: 지난3달 
	* 4: 지난1년


## Usage

```html
<template>
    <div>
        <!-- 옵션설정 안하는 경우 (default today) -->
        <DatePicker v-on:datePick="changeDatePicker" ref="commonDatePicker">기간</DatePicker>
        <!-- 옵션설정 하는 경우 -->
        <DatePicker v-on:datePick="changeDatePicker" ref="commonDatePicker" v-bind:optionsProps="[0, 2, 4]">기간</DatePicker>
    </div>
</template>

<script>
import DatePicker from './DatePicker';
	
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
