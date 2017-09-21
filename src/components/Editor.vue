<template>
  <div id="editor">
    <ul class="tab">
      <li v-for="i in [0,1,2,3,4,5]" v-bind:class="{active: currentTab === i}" v-on:click="currentTab = i">
        <svg class="icon" aria-hidden="true">
          <use v-bind:xlink:href="'#icon-'+icons[i]+''"></use>
        </svg>
      </li>
    </ul>
    <ul class="content">
      <li v-bind:class="{active: currentTab === 0}">
        <h2>个人信息</h2>
        <el-form>
          <el-form-item label="姓名">
            <el-input v-model="profile.name"></el-input>
          </el-form-item>
          <el-form-item label="城市">
            <el-input v-model="profile.city"></el-input>
          </el-form-item>
          <el-form-item label="出生年月">
            <el-input v-model="profile.birth"></el-input>
          </el-form-item>
        </el-form>
      </li>
      <li v-bind:class="{active: currentTab === 1}">
        <h2>工作经历</h2>
        <el-form class="work-form">
          <div v-for="(work, index) in workHistory" class="work-item">
            <i class="el-icon-circle-close work-close" v-on:click="removeWorkHistory(index)"></i>
            <el-form-item label="公司">
              <el-input v-model="work.company" class="work-input"></el-input>
            </el-form-item>
            <el-form-item label="工作内容">
              <el-input v-model="work.content"></el-input>
            </el-form-item>
            <hr>
          </div>
          <el-button type="success" v-on:click="addWorkHistory()" class="work-btn">Add</el-button>
        </el-form>
      </li>
      <li v-bind:class="{active: currentTab === 2}">
        <h2>学习经历</h2>
        <el-form class="work-form">
          <div v-for="(study, index) in studyInfo" class="work-item">
            <i class="el-icon-circle-close work-close" v-on:click="removeStudy(index)"></i>
            <el-form-item label="学校">
              <el-input v-model="study.school" class="work-input"></el-input>
            </el-form-item>
            <el-form-item label="时间">
              <el-input v-model="study.duration"></el-input>
            </el-form-item>
            <el-form-item label="学位">
              <el-input v-model="study.degree"></el-input>
            </el-form-item>
            <hr>
          </div>
          <el-button type="success" v-on:click="addStudy()" class="work-btn">Add</el-button>
        </el-form>
      </li>
      <li v-bind:class="{active: currentTab === 3}">
        <h2>项目经历</h2>
        <el-form class="work-form">
          <div v-for="(project, index) in projectInfo" class="work-item">
            <i class="el-icon-circle-close work-close" v-on:click="removeProject(index)"></i>
            <el-form-item label="项目名称">
              <el-input v-model="project.name" class="work-input"></el-input>
            </el-form-item>
            <el-form-item label="工作内容">
              <el-input v-model="project.content"></el-input>
            </el-form-item>
            <hr>
          </div>
          <el-button type="success" v-on:click="addProject()" class="work-btn">Add</el-button>
        </el-form>
      </li>
      <li v-bind:class="{active: currentTab === 4}">
        <h2>获奖情况</h2>
        <el-form class="work-form">
          <div v-for="(prize, index) in prizeInfo" class="work-item">
            <i class="el-icon-circle-close work-close" v-on:click="removePrize(index)"></i>
            <el-form-item label="获奖情况">
              <el-input v-model="prize.information" class="work-input"></el-input>
            </el-form-item>
          </div>
          <el-button type="success" v-on:click="addPrize()" class="work-btn">Add</el-button>
        </el-form>
      </li>
      <li v-bind:class="{active: currentTab === 5}">
        <h2>联系方式</h2>
        <el-form class="work-form">
          <div v-for="(contact, index) in contactInfo" class="work-item">
            <i class="el-icon-circle-close work-close" v-on:click="removeContact(index)"></i>
            <el-form-item label="邮箱">
              <el-input v-model="contact.mail" class="work-input"></el-input>
            </el-form-item>
            <el-form-item label="手机号码">
              <el-input v-model="contact.phoneNumber"></el-input>
            </el-form-item>
            <el-form-item label="QQ">
              <el-input v-model="contact.qq"></el-input>
            </el-form-item>
            <hr>
          </div>
          <el-button type="success" v-on:click="addContact()" class="work-btn">Add</el-button>
        </el-form>
      </li>
    </ul>
  </div>
</template>

<style lang="scss">
  #editor {
    display: flex;
    .tab {
      width: 25%;
      height: 100%;
      text-align: center;
      border-right: 1px solid rgb(68, 68, 68);
      li {
        border-bottom: 1px solid rgb(68, 68, 68);
        height: calc(100% / 6);
        display: flex;
        align-items: center;
        justify-content: center;
        &:last-child {
          border: none;
        }
        &.active {
          background: #13ce66;
          .icon {
            fill: white;
          }
        }
      }
    }
    .content {
      width: 75%;
      height: 100%;
      overflow: auto;
      li {
        width: 100%;
        display: none;
        &.active {
          display: flex;
          flex-direction: column;
          justify-content: center;
          align-items: center;
        }
        h2{
          margin: 2rem;
          font-size: 2rem;
        }
        .work-form{
          width: 80%;
        }
        input:focus{
          border: 1px solid #13ce66;
        }
        :nth-child(2){
          .work-btn{
            display: block;
            margin: 0 auto;
          }
        }
        hr{
          margin-bottom: 2rem;
        }
        .work-item{
          position: relative;
          .work-close{
            position: absolute;
            right: 0;
            top: 0;
            z-index: 2;
          }
        }
      }
    }
  }
  .icon {
    width: 4em;
    height: 4em;
    vertical-align: -0.15em;
    fill: #373737;
    overflow: hidden;
  }
</style>

<script>
  export default {
    data() {
      return {
        currentTab: 0,
        icons: ['shenfenzheng', 'work', 'book', 'heart', 'jiangbei', 'phone'],
        profile:{
          name: '',
          city: '',
          birth: ''
        },
        workHistory: [
          {company: '', content: ''}
        ],
        studyInfo: [
          {school: '', duration: '', degree: ''}
        ],
        projectInfo: [
          {name: '', content: ''}
        ],
        prizeInfo: [
          {information: ''}
        ],
        contactInfo: [
          {mail: '', phoneNumber: '', qq: ''}
        ]
      }
    },
    methods:{
      addWorkHistory(){
        this.workHistory.push({
          company: '',
          content: ''
        })
      },
      removeWorkHistory(index){
        this.workHistory.splice(index, 1);
      },
      addStudy(){
        this.studyInfo.push({
          school: '',
          duration: '',
          degree: ''
        })
      },
      removeStudy(index){
        this.studyInfo.splice(index, 1);
      },
      addProject(){
        this.projectInfo.push({
          name: '',
          content: ''
        })
      },
      removeProject(index){
        this.projectInfo.splice(index, 1);
      },
      addPrize(){
        this.prizeInfo.push({
          information: ''
        })
      },
      removePrize(index){
        this.prizeInfo.splice(index, 1);
      },
      addContact(){
        this.contactInfo.push({
          mail: '',
          phoneNumber: '',
          qq: ''
        })
      },
      removeContact(index){
        this.contactInfo.splice(index, 1);
      }
    }
  }
</script>
