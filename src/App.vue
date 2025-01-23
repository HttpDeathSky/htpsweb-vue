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
  methods: {
    showMessage() {
      this.$message({
        message: 'Button Clicked!',
        type: 'success'
      });
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
