<template>
  <div class="juzhogn">
    <!-- {{ dialogFormVisible }} -->
    <el-table :data="tableData" border style="width: 100%">
      <el-table-column fixed prop="data" label="日期" width="150">
      </el-table-column>
      <el-table-column prop="name" label="姓名" width="120"> 
      </el-table-column>
      <el-table-column prop="province" label="省份" width="120">
      </el-table-column>
      <el-table-column prop="city" label="市区" width="120"> </el-table-column>
      <el-table-column prop="address" label="地址" width="300">
      </el-table-column>
      <el-table-column prop="zip" label="邮编" width="120"> </el-table-column>
      <el-table-column fixed="right" label="操作" width="100">
        <template slot-scope="scope">
          <el-button type="text" @click="handleEdit(scope.row)">查看</el-button>
          <el-button type="text" @click="dialogFormVisible = true"
            >编辑</el-button
          >
        </template>
      </el-table-column>
    </el-table>
    <!-- 新增数据弹框 -->
    <el-dialog title="列表信息" :visible.sync="dialogFormVisible">
      <el-form
        :model="form"
        class="ConName"
        ref="form"
        :before-close="disableClose"
      >
        <el-form-item label="日期" prop="data">
          <el-input maxlength="50" autocomplete="on" v-model="form.data"  />
        </el-form-item>
      </el-form>
      <el-form
        :model="form"
        class="ConName"
        ref="form"
        :before-close="disableClose"
      >
        <el-form-item label="姓名" prop="name">
          <el-input maxlength="50" autocomplete="on" v-model="form.name" />
        </el-form-item>
      </el-form>
      <el-form
        :model="form"
        class="ConName"
        ref="form"
        :before-close="disableClose"
      >
        <el-form-item label="省份" prop="province">
          <el-input maxlength="50" autocomplete="on" v-model.trim="form.province" />
        </el-form-item>
      </el-form>
      <el-form
        :model="form"
        class="ConName"
        ref="form"
        :before-close="disableClose"
      >
        <el-form-item label="市区" prop="province">
          <el-input maxlength="50" autocomplete="on" v-model="form.city" />
        </el-form-item>
      </el-form>
      <el-form
        :model="form"
        class="ConName"
        ref="form"
        :before-close="disableClose"
      >
        <el-form-item label="地址" prop="province">
          <el-input maxlength="50" autocomplete="on" v-model="form.address" />
        </el-form-item>
      </el-form>
      <el-form
        :model="form"
        class="ConName"
        ref="form"
        :before-close="disableClose"
      >
        <el-form-item label="邮编" prop="province">
          <el-input maxlength="50" autocomplete="on" v-model="form.zip" />
        </el-form-item>
      </el-form>
      <div class="dialog-footer">
        <el-button @click="dialogFormVisible = false">取消</el-button>
        <el-button @click="sayyes()" type="primary">确定</el-button>
      </div>
    </el-dialog>
    <!-- 结束 -->
  </div>
</template>

<script>
import { reqCategoryList } from "../API/index";

export default {
  data() {
    return {
      tableData: [],
      
      dialogFormVisible: false,
      springframe: [
        { label: "日期", prop: "data" },
        { label: "姓名", prop: "name" },
        { label: "市区", prop: "city" },
        { label: "邮编", prop: "zip" },
        { label: "地址", prop: "address" },
      ],
      form: {},
    };
  },
  methods: {
    //点击取消弹窗关闭
    quxiao() {
      this.$reqCategoryList.dialogFormVisible = false;
      console.log(this.dialogFormVisible);
    },
    onClickInfo() {
      this.dialogFormVisible = true;
      console.log("---eeeeeeeee---->", this.dialogFormVisible);
    },
    //编辑
    handleEdit(rows) {
      this.dialogFormVisible = true;
      // this.$emit("handleEditDevive", i, rows);
      // console.log("---111----->", rows);
      this.form = { ...rows };
      // { ...rows }（扩展运算符）
    },
    disableClose() {
      this.disableForm = {};
      this.$refs["disableForm"].clearValidate();
      this.dialogDisable = false;
    },
    dialogVisible() {
      this.dialogVisible = false;
    },
    sayyes() {
      this.dialogFormVisible = false;
    },
  },
  mounted() {
    reqCategoryList().then((data) => {
      console.log("数据内容>>>>>", data.data);
      this.tableData = data.data;
    });
  },
};
</script>
<style >
.juzhogn {
  margin: 0 auto;
  max-width: 1035px;
}
.el-form-item__content {
  display: flex;
  justify-content: space-around;
}
</style>