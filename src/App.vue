<template>
  <el-container style="height: 100vh; background-color: #f4f7fc;">
    <!-- Header -->
    <el-header style="background-color: #409EFF; color: white;">
      <div class="logo" style="font-size: 24px; font-weight: bold;">Vue + Element Plus</div>
    </el-header>

    <!-- Main Content -->
    <el-main>
      <el-row :gutter="20" style="margin-top: 20px;">
        <!-- Card 1 -->
        <el-col :span="8">
          <el-card shadow="hover" style="border-radius: 8px;">
            <template v-slot:header>
              <div class="card-header">Card 1</div>
            </template>
            <div class="card-content">
              <p>This is some content inside the first card.</p>
              <el-button type="primary" @click="showMessage">Click Me</el-button>
            </div>
          </el-card>
        </el-col>

        <!-- Form Card -->
        <el-col :span="8">
          <el-card shadow="hover" style="border-radius: 8px;">
            <template v-slot:header>
              <div class="card-header">Form Section</div>
            </template>
            <div class="card-content">
              <el-form :model="form" ref="formRef" label-width="120px">
                <!-- Name Field -->
                <el-form-item label="名称" prop="name" :rules="[{ required: true, message: '请输入名称', trigger: 'blur' }]">
                  <el-input v-model="form.name" placeholder="请输入名称"></el-input>
                </el-form-item>

                <!-- Effective Time Field -->
                <el-form-item label="生效时间" prop="effectiveTime"
                  :rules="[{ required: true, message: '请选择生效时间', trigger: 'change' }]">
                  <el-date-picker v-model="form.effectiveTime" type="datetime" placeholder="请选择生效时间"></el-date-picker>
                </el-form-item>

                <!-- Remaining Time Field -->
                <el-form-item label="剩余时间">
                  <el-input v-model="form.remainingTime" placeholder="剩余时间" disabled></el-input>
                </el-form-item>

                <!-- Add Button -->
                <el-form-item>
                  <el-button type="primary" @click="addForm">新增</el-button>
                </el-form-item>
              </el-form>
            </div>
          </el-card>
        </el-col>

        <!-- Card 2 -->
        <el-col :span="8">
          <el-card shadow="hover" style="border-radius: 8px;">
            <template v-slot:header>
              <div class="card-header">Card 2</div>
            </template>
            <div class="card-content">
              <p>This is some content inside the second card.</p>
              <el-button type="primary" @click="showMessage">Click Me</el-button>
            </div>
          </el-card>
        </el-col>

        <!-- Card 3 -->
        <el-col :span="8">
          <el-card shadow="hover" style="border-radius: 8px;">
            <template v-slot:header>
              <div class="card-header">Card 3</div>
            </template>
            <div class="card-content">
              <p>This is some content inside the third card.</p>
              <el-button type="primary" @click="showMessage">Click Me</el-button>
            </div>
          </el-card>
        </el-col>
      </el-row>
    </el-main>

    <!-- Footer -->
    <el-footer style="text-align: center; background-color: #409EFF; color: white; padding: 10px;">
      <div>&copy; 2025 Vue + Element Plus Example</div>
    </el-footer>
  </el-container>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      // Form model data
      form: {
        name: '',
        effectiveTime: '',
        remainingTime: ''
      }
    };
  },
  methods: {
    showMessage() {
      this.$message({
        message: 'Button Clicked!',
        type: 'success'
      });
    },
    // Method to handle form submission
    addForm() {
      // Calculate remaining time (simple example, can be modified)
      if (this.form.effectiveTime) {
        const currentTime = new Date();
        const effectiveTime = new Date(this.form.effectiveTime);
        const remaining = Math.max((effectiveTime - currentTime) / 1000, 0); // remaining time in seconds
        this.form.remainingTime = `${remaining.toFixed(0)} seconds`;

        // If form is valid, show success message
        this.$refs.formRef.validate((valid) => {
          if (valid) {
            this.$message({
              message: 'Form submitted successfully!',
              type: 'success'
            });
          } else {
            this.$message.error('Please fill in the form correctly');
            return false;
          }
        });
      } else {
        this.$message.error('Please select an effective time');
      }
    }
  }
}
</script>

<style scoped>
.card-header {
  font-size: 18px;
  font-weight: bold;
  color: #409EFF;
}

.card-content {
  padding: 20px;
  font-size: 14px;
  color: #333;
}

.card-content p {
  margin-bottom: 20px;
}

.el-button {
  width: 100%;
}

.el-footer {
  font-size: 14px;
  color: #fff;
}
</style>
