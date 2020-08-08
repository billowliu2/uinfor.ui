<template>
  <um-box page>
    <el-row>
      <um-button text="默认按钮"></um-button>
      <um-button type="primary" text="主要按钮"></um-button>
      <um-button type="success" text="成功按钮"></um-button>
      <um-button type="info" text="信息按钮"></um-button>
      <um-button type="warning" text="警告按钮"></um-button>
      <um-button type="danger" text="危险按钮"></um-button>
    </el-row>

    <el-row>
      <um-button plain text="朴素按钮"></um-button>
      <um-button type="primary" plain text="主要按钮"></um-button>
      <um-button type="success" plain text="成功按钮"></um-button>
      <um-button type="info" plain text="信息按钮"></um-button>
      <um-button type="warning" plain text="警告按钮"></um-button>
      <um-button type="danger" plain text="危险按钮"></um-button>
    </el-row>

    <el-row>
      <um-button round text="圆角按钮"></um-button>
      <um-button type="primary" round text="主要按钮"></um-button>
      <um-button type="success" round text="成功按钮"></um-button>
      <um-button type="info" round text="信息按钮"></um-button>
      <um-button type="warning" round text="警告按钮"></um-button>
      <um-button type="danger" round text="危险按钮"></um-button>
    </el-row>

    <el-row>
      <um-button icon="search" circle></um-button>
      <um-button type="primary" icon="edit" circle></um-button>
      <um-button type="success" icon="select" circle></um-button>
      <um-button type="info" icon="permission" circle></um-button>
      <um-button type="warning" icon="refresh" circle></um-button>
      <um-button type="danger" icon="delete" circle></um-button>
    </el-row>
    <el-row>
      <um-button type="text" text="文字按钮"></um-button>
      <um-button type="text" text="文字按钮" disabled></um-button>
    </el-row>
    <el-row>
      <um-button type="primary" icon="edit"></um-button>
      <um-button type="primary" icon="search" text="搜索"></um-button>
      <um-button type="primary">
        刷新
        <um-icon name="refresh"></um-icon>
      </um-button>
    </el-row>
    <el-row>
      <el-button-group>
        <um-button type="primary" icon="arrow-left" text="上一页"></um-button>
        <um-button type="primary">
          下一页
          <um-icon name="arrow-right"></um-icon>
        </um-button>
      </el-button-group>
      <el-button-group>
        <um-button type="primary" icon="edit"></um-button>
        <um-button type="primary" icon="preview"></um-button>
        <um-button type="primary" icon="delete"></um-button>
      </el-button-group>
    </el-row>
    <el-row>
      <um-button type="primary" :loading="true" text="加载中"></um-button>
    </el-row>
    <el-row>
      <el-alert title="按钮尺寸" type="warning" description="按钮默认尺寸根据系统的字号大小设置" show-icon :closable="false"></el-alert>
      <um-button text="默认按钮"></um-button>
      <um-button text="中等按钮" size="medium"></um-button>
      <um-button text="小型按钮" size="small"></um-button>
      <um-button text="超小按钮" size="mini"></um-button>
    </el-row>
  </um-box>
</template>
<style></style>
