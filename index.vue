<!-- 时刻表 -->

<template>
  <div class="container">
    <div class="weekZHContainer">
      <div class="weekZh" v-for="(wzItem, wzIndex) in weekZH" :key="wzIndex">
        {{ wzItem }}
      </div>
    </div>
    <div class="column" v-for="(r, index) in res" :key="index">
      <div class="timeContainer">
        <!-- 时间 -->
        <div class="time">{{ r.SDMC }}</div>
        <!-- 遍历week -->
        <div v-for="(weItem, wIndex) in weekEN" :key="wIndex">
          <!-- 遍历对象 -->
          <div
            class="school"
            v-for="(rVal, rKey, rIndex) in r"
            :key="rIndex"
            v-show="rKey !== 'SDMC' && rKey === weItem"
          >
            {{ rVal }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {},
  data() {
    return {
      weekZH: ["", "周一", "周二", "周三", "周四", "周五", "周六", "周日"],
      weekEN: [
        "MONDAY",
        "TUESDAY",
        "WEDNESDAY",
        "THURSDAY",
        "FRIDAY",
        "SATURDAY",
        "SUNDAY"
      ],
      // 接口返回数据
      res: [
        {
          MONDAY: "",
          SUNDAY: "",
          WEDNESDAY: "",
          SDMC: "14:00-15:00",
          THURSDAY: "",
          SATURDAY: "",
          TUESDAY: "仙林校区",
          FRIDAY: ""
        },
        {
          MONDAY: "",
          SUNDAY: "",
          WEDNESDAY: "",
          SDMC: "15:30-16:30",
          THURSDAY: "江宁校区",
          SATURDAY: "",
          TUESDAY: "",
          FRIDAY: ""
        },
        {
          MONDAY: "",
          SUNDAY: "",
          WEDNESDAY: "嘉定校区",
          SDMC: "10:00-11:00",
          THURSDAY: "",
          SATURDAY: "",
          TUESDAY: "",
          FRIDAY: "四平校区"
        },
        {
          MONDAY: "",
          SUNDAY: "",
          WEDNESDAY: "",
          SDMC: "08:30-09:30",
          THURSDAY: "浦口校区",
          SATURDAY: "",
          TUESDAY: "",
          FRIDAY: ""
        }
      ]
    };
  },
  components: {},
  computed: {},
  watch: {},
  methods: {
    // 初始化
    init() {
      // 按时间排序
      this.res = this.res.sort((a, b) => {
        return a.SDMC > b.SDMC ? 1 : -1;
      });
    }
  },
  mounted() {
    this.init();
  }
};
</script>

<style scoped lang="scss">
.container {
  display: flex;
  .weekZHContainer {
    .weekZh {
      height: 25px;
      outline: 1px dashed #000;
    }
  }
  .column {
    margin: 0 5px;
    text-align: center;
    line-height: 25px;
    .time {
      height: 25px;
      outline: 1px dashed #000;
    }
    .school {
      height: 25px;
      outline: 1px dashed #000;
    }
  }
}
</style>
