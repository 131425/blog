---
layout: posts
title: vue-elementUI展开表格手风琴效果实现
date: 2018-07-18 17:14:31
tags:
---

> elementUI 可展开表格手风琴效果实现

```javascript
<template>
    <el-table
        :data="tableData5"
        style="width: 100%"
        row-key="id"
        @row-click="rowClick">
        <el-table-column type="expand">
            <template slot-scope="props">
                <el-form label-position="left" inline class="demo-table-expand">
                    <el-form-item label="商品名称">
                        <span>{{ props.row.name }}</span>
                    </el-form-item>
                    <el-form-item label="所属店铺">
                        <span>{{ props.row.shop }}</span>
                    </el-form-item>
                    <el-form-item label="商品 ID">
                        <span>{{ props.row.id }}</span>
                    </el-form-item>
                    <el-form-item label="店铺 ID">
                        <span>{{ props.row.shopId }}</span>
                    </el-form-item>
                    <el-form-item label="商品分类">
                        <span>{{ props.row.category }}</span>
                    </el-form-item>
                    <el-form-item label="店铺地址">
                        <span>{{ props.row.address }}</span>
                    </el-form-item>
                    <el-form-item label="商品描述">
                        <span>{{ props.row.desc }}</span>
                    </el-form-item>
                </el-form>
            </template>
        </el-table-column>
        <el-table-column
            label="商品 ID"
            prop="id">
        </el-table-column>
        <el-table-column
            label="商品名称"
            prop="name">
        </el-table-column>
        <el-table-column
            label="描述"
            prop="desc">
        </el-table-column>
    </el-table>
</template>

<script>
  export default {
    data() {
      return {
          tableData5: [{
              id: '12987122',
              name: '好滋好味鸡蛋仔',
              category: '江浙小吃、小吃零食',
              desc: '荷兰优质淡奶，奶香浓而不腻',
              address: '上海市普陀区真北路',
              shop: '王小虎夫妻店',
              shopId: '10333'
          }, {
              id: '12987126',
              name: '好滋好味鸡蛋仔',
              category: '江浙小吃、小吃零食',
              desc: '荷兰优质淡奶，奶香浓而不腻',
              address: '上海市普陀区真北路',
              shop: '王小虎夫妻店',
              shopId: '10333'
          }],
          expands: [],// 要展开的行，数值的元素是row的key值
      }
    },
    methods:{
        //在<table>里，已经设置row的key值设置为每行数据 id：row-key="id" (必须唯一哟)
          rowClick(row, event, column) {
              Array.prototype.remove = function (val) {
                let index = this.indexOf(val);
                if (index > -1) {
                    this.splice(index, 1);
                }
              };
              if (this.expands.indexOf(row.id) < 0) {
                  //实现展开当前行的时候，其他行都能收起来 所以要清空数组
                  this.expands = []; 
                  this.expands.push(row.id);
              } else {
                  this.expands.remove(row.id);
              }
          }
      }

  }
</script>
```

