<template>
  <view>
    <uni-section title="外出信息" type="line">
      <view>
        <uni-forms
          style="margin: 0px 10px 0px 10px"
          :modelValue="msg"
          labelPosition="left"
          label-width="80px"
        >
          <uni-forms-item label="开始日期" required>
            <uni-datetime-picker
              type="date"
              v-model="msg.startDate"
              :clear-icon="false"
            />
          </uni-forms-item>
          <uni-forms-item label="结束日期" required>
            <uni-datetime-picker
              type="date"
              v-model="msg.endDate"
              :clear-icon="false"
            />
          </uni-forms-item>
          <uni-forms-item label="外出地点" required>
            <uni-easyinput
              v-model="msg.place"
              :clearSize="18"
              placeholder="请输入外出地点,最好不要太长"
            />
          </uni-forms-item>
          <uni-forms-item label="外出原因" required>
            <uni-easyinput
              type="textarea"
              v-model="msg.reason"
              placeholder="请输入外出原因"
            />
          </uni-forms-item>
        </uni-forms>
      </view>
    </uni-section>
    <uni-section title="个人信息" type="line">
      <view>
        <uni-forms
          style="margin: 0px 10px 0px 10px"
          :modelValue="student"
          labelPosition="left"
          label-width="80px"
        >
          <uni-forms-item label="姓名" required>
            <uni-easyinput
              v-model="student.name"
              :clearSize="18"
              placeholder="请输入姓名"
            />
          </uni-forms-item>
          <uni-forms-item label="学号" required>
            <uni-easyinput
              v-model="student.id"
              :clearSize="18"
              placeholder="请输入学号"
            />
          </uni-forms-item>
          <uni-forms-item label="学院" required>
            <uni-easyinput
              v-model="student.college"
              :clearSize="18"
              placeholder="请输入学院"
            />
          </uni-forms-item>
          <uni-forms-item label="年级" required>
            <uni-easyinput
              v-model="student.grade"
              :clearSize="18"
              placeholder="请输入年级"
            />
          </uni-forms-item>
          <uni-forms-item label="人员类型" required>
            <uni-easyinput
              v-model="student.type"
              :clearSize="18"
              placeholder="请输入人员类型"
            />
          </uni-forms-item>
        </uni-forms>
      </view>
    </uni-section>
    <button type="primary" @click="btnSubmit()">保存</button>
    <uni-popup ref="popup" type="message">
      <uni-popup-message mode="success" message="保存成功" :duration="5000">
      </uni-popup-message>
    </uni-popup>
  </view>
</template>

<script>
export default {
  data() {
    return {
      msg: {
        startDate: new Date().toISOString().slice(0, 10),
        endDate: new Date().toISOString().slice(0, 10),
        place: "天河区中山三院",
        reason: "去医院看胃病",
      },

      student: {
        name: "张三",
        id: "202005201314",
        college: "土木与交通学院",
        grade: "2020级",
        type: "本科生",
      },
    };
  },
  created() {
    const msg = uni.getStorageSync("msg");
    const student = uni.getStorageSync("student");
    if (msg) {
      this.msg = msg;
    }
    if (student) {
      this.student = student;
    }
  },
  methods: {
    btnSubmit() {
      uni.setStorageSync("msg", this.msg);
      uni.setStorage({
        key: "student",
        data: this.student,
      });
      this.$refs.popup.open("top");
    },
  },
};
</script>

<style></style>
