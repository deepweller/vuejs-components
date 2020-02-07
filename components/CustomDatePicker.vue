<template>
  <div class="block">
    <span class="demonstration">
      <slot> </slot>
    </span>
    <el-date-picker
      v-model="value"
      type="daterange"
      value-format="yyyy-MM-dd"
      align="right"
      unlink-panels
      range-separator="~"
      start-placeholder="시작일"
      end-placeholder="종료일"
      :picker-options="pickerOptions"
      v-on:change="changeDate"
    >
    </el-date-picker>
  </div>
</template>

<script>
const options = [
  {
    text: '오늘',
    onClick(picker) {
      const now = new Date();
      picker.$emit('pick', [now, now]);
    }
  },
  {
    text: '지난주',
    onClick(picker) {
      const end = new Date();
      const start = new Date();
      start.setTime(start.getTime() - 3600 * 1000 * 24 * 7);
      picker.$emit('pick', [start, end]);
    }
  },
  {
    text: '지난달',
    onClick(picker) {
      const end = new Date();

      let start = new Date();
      let mm = start.getMonth() - 1;
      if (mm < 0) {
        mm += 12;
        start.setFullYear(start.getFullYear() - 1);
      }
      start.setMonth(mm);

      picker.$emit('pick', [start, end]);
    }
  },
  {
    text: '지난3달',
    onClick(picker) {
      const end = new Date();

      let start = new Date();
      let mm = start.getMonth() - 3;
      if (mm < 0) {
        mm += 12;
        start.setFullYear(start.getFullYear() - 1);
      }
      start.setMonth(mm);

      picker.$emit('pick', [start, end]);
    }
  },
  {
    text: '지난1년',
    onClick(picker) {
      const end = new Date();

      let start = new Date();
      start.setFullYear(start.getFullYear() - 1);

      picker.$emit('pick', [start, end]);
    }
  }
];

export default {
  props: ['optionsProps'],
  data() {
    return {
      pickerOptions: {
        shortcuts: []
      },
      value: ''
    };
  },
  created() {
    this.setNowDt();
    this.setPickerOption();
  },
  methods: {
    setPickerOption() {
      if (this.optionsProps === undefined || this.optionsProps.length === 0) {
        this.pickerOptions.shortcuts.push(options[0]);
      } else {
        for (let i = 0; i < this.optionsProps.length; i++) {
          this.pickerOptions.shortcuts.push(options[this.optionsProps[i]]);
        }
      }
    },
    changeDate() {
      this.$emit('datePick', this.value);
    },
    setNowDt() {
      const now = new Date();
      const yyyy = now.getFullYear();
      let mm = now.getMonth() + 1;
      let dd = now.getDate();

      if (mm < 10) mm = '0' + mm;
      if (dd < 10) dd = '0' + dd;

      const date = yyyy + '-' + mm + '-' + dd;
      this.value = [date, date];

      this.changeDate();
    }
  }
};
</script>
