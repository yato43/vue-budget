<template>
  <ElCard class="form-card">
    <ElForm :model="formData" ref="addItemForm" :rules="rules" label-position="top">
      <ElFormItem label="Type" prop="type">
        <ElSelect class="type-select" v-model="formData.type" placeholder="Choose type...">
          <ElOption label="Income" value="INCOME"></ElOption>
          <ElOption label="Outcome" value="OUTCOME"></ElOption>
        </ElSelect>
      </ElFormItem>
      <ElFormItem label="Comments" prop="comment">
        <ElInput v-model="formData.comment"></ElInput>
      </ElFormItem>
      <ElFormItem label="Value" prop="value">
        <ElInput v-model.number="formData.value"></ElInput>
      </ElFormItem>
      <ElButton @click="onSubmit" type="primary">Submit</ElButton>
    </ElForm>
  </ElCard>
</template>

<script>
function typeChecker(obj) {
  if (obj.type === 'INCOME'){
    return obj
  }else if (obj.type === 'OUTCOME'){
    if (obj.value > 0){
      obj.value *= -1
      return obj
    }else{
      return obj
    }
  }
}

export default {
  name: "FormMain",
  data: () => ({
    formData: {
      type: 'INCOME',
      comment: '',
      value: 0,
    },
    rules: {
      type: [
        {required: true, message: 'Please select type', trigger: "blur"}
      ],
      comment: [
        {required: true, message: 'Please input type', trigger: "blur"}
      ],
      value: [
        {required: true, message: 'Please input type', trigger: "blur"},
        {type: 'number', required: true, message: 'Value must be a number', trigger: "blur"}
      ],
    },
  }),
  methods: {
    onSubmit() {
      this.$refs.addItemForm.validate((valid) => {
        if (valid) {
          this.$emit('submitForm', {...typeChecker(this.formData)});
          this.$refs.addItemForm.resetFields();
        }
      });
    },
  },
}
</script>

<style scoped>
.form-card {
  max-width: 500px;
  margin: auto;
}

.type-select {
  width: 100%;
}
</style>
