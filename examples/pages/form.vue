<template lang="pug">
  .input
    //- 标题
    q-row(position="fixed" t=0 l=0 col=100 zIndex=1)
      q-head-bar(
        bkColor="deepskyblue"
        color="#fff"
        :leftArrow="true"
        centerText="q-form"
        :rightEmpty="true")
    q-row(h=12)
    q-row(pl=2 pr=2)
      //- demo演示
      q-row(tag="section")
        q-cell(
          leftIcon="q-icon icon-tagfill"
          leftIconColor="deepskyblue"
          title="Demo演示"
          fontSize=16
          :borderBottom="true")
        q-row(fontSize=14 lh=9 mb=2)
          |控制表单的组件有两个,一个<main>q-form</main>,一个<main>q-input</main>,
          |这两个组件优势体现在,一个是验证,验证提供了友好的api,不用根据类型一个一个调用事件,
          |第二个优势是移动端的键盘类型,通过<main>type</main>传的值可以判断到底是提供数字键盘、字符键盘、搜索键盘
          |我们来看几个列子
        //- 列子
        q-row(tag="section")
          q-row(tag="section")
            q-cell(
              leftIcon="q-icon icon-edit"
              leftIconColor="deepskyblue"
              title="不需要验证的表单")
            q-form(ref="myForm1")
              q-row(h=12 dir="left" align="center")
                q-row(w=15 align="center" justify="center") 名字:
                q-input(v-model="noFormat.name" placeholder="请输入你的名字")
              q-row(h=12 dir="left" align="center")
                q-row(w=15 align="center" justify="center") 年龄:
                q-input(type="integer" v-model="noFormat.age" placeholder="请输入你的年龄")
              q-row(h=12 justify="flex-end" align="center")
                q-row(
                  row=80 col=40
                  bkColor="deepskyblue"
                  :radius="20"
                  justify="center"
                  align="center"
                  @clicked="submit1")
                  q-col(color="white") 提交
            q-row(mt=4) <main>template</main>
            q-code(type="html").
              &ltq-form ref="myForm1"&gt
                &ltq-row h=12 dir="left" align="center"&gt
                  &ltq-row w=15 align="center" justify="center"&gt名字:&lt/q-row&gt
                  &ltq-input v-model="noFormat.name" placeholder="请输入你的名字"&gt&lt/q-input&gt
                &lt/q-row&gt
                &ltq-row h=12 dir="left" align="center"&gt
                  &ltq-row w=15 align="center" justify="center"&gt年龄:&lt/q-row&gt
                  &ltq-input type="integer" v-model="noFormat.age" placeholder="请输入你的年龄"&gt&lt/q-input&gt
                &lt/q-row&gt
                &ltq-row h=12 justify="flex-end" align="center"&gt
                  &ltq-row
                    row=80 col=40
                    bkColor="deepskyblue"
                    :radius="20"
                    justify="center"
                    align="center"
                    @clicked="submit1"&gt
                    &ltq-col color="white"&gt提交&lt/q-col&gt
                  &lt/q-row&gt
                &lt/q-row&gt
              &lt/q-form&gt
            main vue
            q-code.
              data() {
                return {
                  noFormat: {
                    name: '',
                    age: ''
                  }
                }
              },
              methods: {
                submit1() {
                  this.$notice.toast(`名字:${this.noFormat.name};年龄:${this.noFormat.age}`)
                }
              }
          q-row(tag="section")
            q-cell(
              leftIcon="q-icon icon-edit"
              leftIconColor="deepskyblue"
              title="需要验证的表单")
            q-form(
              ref="myForm2"
              :model="format"
              :rules="rules")
              q-row(h=12 dir="left" align="center")
                q-row(w=15 align="center" justify="center") 名字:
                q-input(
                  prop="name" v-model="format.name" placeholder="名字长度在3到5个字符")
              q-row(h=12 dir="left" align="center")
                q-row(w=15 align="center" justify="center") 电话:
                q-input(
                  prop="tel" type="tel"
                  v-model="format.tel" placeholder="请输入你的电话")
              q-row(h=12 justify="flex-end" align="center")
                q-row(
                  row=80 col=40
                  bkColor="deepskyblue"
                  :radius="20"
                  justify="center"
                  align="center"
                  @clicked="submit2")
                  q-col(color="white") 提交
            q-row(mt=4) <main>template</main>
            q-code(type="html").
              &ltq-form ref="myForm2" :model="format" :rules="rules"&gt
                &ltq-row h=12 dir="left" align="center"&gt
                  &ltq-row w=15 align="center" justify="center"&gt名字:&lt/q-row&gt
                  &ltq-input
                    prop="name" v-model="format.name" placeholder="名字长度在3到5个字符"&gt&lt/q-input&gt
                &lt/q-row&gt
                &ltq-row h=12 dir="left" align="center"&gt
                  &ltq-row w=15 align="center" justify="center"&gt电话:&lt/q-row&gt
                  &ltq-input
                    prop="tel" type="tel"
                    v-model="format.tel" placeholder="请输入你的电话"&gt&lt/q-input&gt
                &lt/q-row&gt
                &ltq-row h=12 justify="flex-end" align="center"&gt
                  &ltq-row
                    row=80 col=40
                    bkColor="deepskyblue"
                    :radius="20"
                    justify="center"
                    align="center"
                    @clicked="submit2"&gt
                    &ltq-col color="white"&gt提交&lt/q-col&gt  
                  &lt/q-row&gt
                &lt/q-row&gt
              &lt/q-form&gt
            main vue
            q-code.
              data() {
                return {
                  format: {
                    name: '',
                    tel: ''
                  },
                  rules: {
                    name: [{
                        required: true,
                        message: '名字不能为空'
                      },
                      {
                        min: 3,
                        max: 5,
                        message: '名字长度在3到5个字符'
                      }
                    ],
                    tel: [{
                        required: true,
                        message: '电话不能为空'
                      },
                      {
                        type: 'tel',
                        message: '请输入正确的电话号码'
                      }
                    ]
                  }
                }
              },
              methods: {
                submit2() {
                  let myForm = this.$refs.myForm2
                  myForm.validate().then((bool) => {
                    if (bool) {
                      this.$notice.toast(`名字:${this.format.name};电话:${this.format.tel}`)
                    }
                  })
                }
              }
      q-row(tag="section")
        q-cell(
          leftIcon="q-icon icon-tagfill"
          leftIconColor="deepskyblue"
          title="API一览"
          fontSize=16
          :borderBottom="true")
        //- Api
        q-row(tag="section")
          q-row(tag="section")
            q-cell(
              leftIcon="q-icon icon-edit"
              leftIconColor="deepskyblue"
              title="q-form")
            q-table(:tableOptions="qForm")
          q-row(tag="section")
            q-cell(
              leftIcon="q-icon icon-edit"
              leftIconColor="deepskyblue"
              title="q-input")
            q-table(:tableOptions="qInput")
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator'
@Component({})
export default class ExInput extends Vue {
  private noFormat: any = {
    name: '',
    age: ''
  }

  private format: any = {
    name: '',
    tel: ''
  }

  private rules: any = {
    name: [
      { required: true, message: '名字不能为空' },
      { min: 3, max: 5, message: '名字长度在3到5个字符' }
    ],
    tel: [
      { required: true, message: '电话不能为空' },
      { type: 'tel', message: '请输入正确的电话号码' }
    ]
  }
  
  private qForm: any = {
    titles: [
      { value: 'Prop' },
      { value: 'Type' },
      { value: 'Required' },
      { value: 'Default' },
      { value: 'Description' }
    ],
    datas: [
      {
        prop: [
          { value: 'model' },
          { value: 'Object' },
          { value: 'Y' },
          { value: '无' },
          { value: '动态绑定的值' }
        ]
      },
      {
        prop: [
          { value: 'rules' },
          { value: 'Object' },
          { value: 'N' },
          { value: '无' },
          { value: '验证规则' }
        ]
      }
    ]
  }

  private qInput: any = {
    titles: [
      { value: 'Prop' },
      { value: 'Type' },
      { value: 'Required' },
      { value: 'Default' },
      { value: 'Description' }
    ],
    datas: [
      {
        prop: [
          { value: 'v-model' },
          { value: 'Any' },
          { value: 'Y' },
          { value: '无' },
          { value: '动态绑定的值' }
        ]
      },
      {
        prop: [
          { value: 'type' },
          { value: 'String' },
          { value: 'N' },
          { value: 'text' },
          { value: '输入框类型' }
        ]
      },
      {
        prop: [
          { value: 'placeholder' },
          { value: 'String' },
          { value: 'N' },
          { value: '' },
          { value: '输入框提醒文字' }
        ]
      },
      {
        prop: [
          { value: 'fix' },
          { value: 'Number' },
          { value: 'N' },
          { value: '4' },
          { value: '默认保留小数位数' }
        ]
      },
      {
        prop: [
          { value: 'prop' },
          { value: 'String' },
          { value: 'N' },
          { value: '无' },
          { value: '验证规则下对应属性名' }
        ]
      },
      {
        prop: [
          { value: 'hasBorder' },
          { value: 'Boolean' },
          { value: 'N' },
          { value: 'false' },
          { value: '是否有全局border' }
        ]
      },
      {
        prop: [
          { value: 'borderBottom' },
          { value: 'Boolean' },
          { value: 'N' },
          { value: 'true' },
          { value: '是否有下border' }
        ]
      },
      {
        prop: [
          { value: 'borderColor' },
          { value: 'String' },
          { value: 'N' },
          { value: '#d6d7dc' },
          { value: 'border颜色' }
        ]
      },
      {
        prop: [
          { value: 'color' },
          { value: 'String' },
          { value: 'N' },
          { value: '无' },
          { value: '字体颜色' }
        ]
      },
      {
        prop: [
          { value: 'bkColor' },
          { value: 'String' },
          { value: 'N' },
          { value: '无' },
          { value: '背景颜色' }
        ]
      }
    ]
  }

  private submit1() {
    this.$notice.toast(`名字:${this.noFormat.name};年龄:${this.noFormat.age}`)
  }

  private submit2() {
    let myForm: any = this.$refs.myForm2
    myForm.validate().then((bool: boolean) => {
      if (bool) {
        this.$notice.toast(`名字:${this.format.name};电话:${this.format.tel}`)
      }
    })
  }
}
</script>