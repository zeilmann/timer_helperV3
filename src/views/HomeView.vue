<template>
    <div class="container">
    <div class="row justify-content-sm-center">
      <div class="col-sm-auto">
        <el-tag v-if="totalB.toFixed(2) === '0.00' || totalB.toFixed(2) === '37.50' || totalB.toFixed(2) === '22.50' || totalB.toFixed(2) === '30.00' || totalB.toFixed(2) === '15.00' || totalB.toFixed(2) === '7.50'" type="success">Hours Calculated: {{ totalB.toFixed(2) }}</el-tag>
        <el-tag v-else type="danger">Hours Calculated: {{ totalB.toFixed(2) }}</el-tag>
        <el-tag v-if ="totalB.toFixed(2) === '0.00'" type="Sucess">the whole week off😄😍😍😍</el-tag>
        <el-tag v-if=" totalB.toFixed(2) === '0.00' || totalB.toFixed(2) === '37.50' || totalB.toFixed(2) === '22.50' || totalB.toFixed(2) === '30.00' || totalB.toFixed(2) === '15.00' || totalB.toFixed(2) === '7.50'" type="success">😄😄</el-tag>
        <el-tag v-else type="danger">😭😭</el-tag>
        <el-tag type="sucess">Days: {{ valorrec1 }}</el-tag>
        <hr>
        <el-button @click="listahorarios()" type="success" round>List</el-button>
        <hr>
        <el-card shadow="always" class="box-card">
          <template #header>
            <div class="card-header">
              <span>Holiday/Sick Day</span>
            </div>
          </template>
          <el-checkbox @change="exibirhorariosMonday()" v-model="SickDay[0]" label="Monday" size="large" />
          <el-checkbox @change="exibirhorariosMonday()" v-model="SickDay[1]" label="Tuesday" size="large" />
          <el-checkbox @change="exibirhorariosMonday()" v-model="SickDay[2]" label="Wednesday" size="large" />
          <el-checkbox @change="exibirhorariosMonday()" v-model="SickDay[3]" label="Thursday" size="large" />
          <el-checkbox @change="exibirhorariosMonday()" v-model="SickDay[4]" label="Friday" size="large" />
        </el-card>
        <hr>
      </div>
    </div>
  </div>

    <!-- SEGUNDA FEIRA -->
  <div v-show="SickDay[0] === false" class="container">
    <div class="row justify-content-sm-center">
      <div class="col-sm-auto">
        <el-card shadow="always" class="box-card">
          <template #header>
            <div class="card-header">
              <span>Monday</span>

            </div>
          </template>
          <div class="demo-range">
            <el-time-picker @change="exibirhorariosMonday(1)" v-model="monday" is-range range-separator="To"
              start-placeholder="Start time" end-placeholder="End time" format="HH:mm" size="small" />
          </div>
          <el-checkbox v-model="SegundaC[0]" label="Lock" size="large" />
          <div>
            <el-collapse v-model="activeName" accordion>
              <el-collapse-item title="Time Off" name="1">
                <div>
                  <div>In Minutes:</div>
                  <el-input-number v-model="numM" @change="exibirhorariosMonday(1)" :min="0"
                    :max="510"></el-input-number>
                </div>
              </el-collapse-item>
            </el-collapse>
          </div>
          <div>
            <el-tag v-if="parseInt(testem) != parseFloat(testem)" class="ml-2" type="danger">Minutes: {{
                testem.toFixed(2)
            }}</el-tag>
            <el-tag v-else class="ml-2" type="success">Minutes: {{ testem.toFixed(2) }}</el-tag>
            <el-tag class="ml-2" type="success">Hours Plus Break: {{ testem2.toFixed(2) }}</el-tag>
            <el-tag class="ml-2" type="warning">Hours:  {{ fixar2(testem2)  }}</el-tag>
          </div>
          <div class="input-group input-group-sm mb-3">
          </div>
        </el-card>
        <hr>
      </div>
      
        </div>
    
  </div>

  <!-- TERCA FEIRA  -->

  <div v-show="SickDay[1] === false" class="container">
    <div class="row justify-content-sm-center">
      <div class="col-sm-auto">
        <el-card class="box-card">
          <template #header>
            <div class="card-header">
              <span>Tuesday</span>

            </div>
          </template>
          <div class="demo-range">
            <el-time-picker @change="exibirhorariosMonday(2)" v-model="tuesday" is-range range-separator="To"
              start-placeholder="Start time" end-placeholder="End time" format="HH:mm" size="small" />
          </div>
          <el-checkbox v-model="SegundaC[1]" label="Lock" size="large" />
          <div>
            <el-collapse v-model="activeNameT" accordion>
              <el-collapse-item title="Time Off" name="1">
                <div>
                  <div>In Minutes:</div>
                  <el-input-number v-model="numT" @change="exibirhorariosMonday(2)" :min="0"
                    :max="510"></el-input-number>
                </div>
              </el-collapse-item>
            </el-collapse>
          </div>
          <div>
            <el-tag v-if="parseInt(testet) != parseFloat(testet)" class="ml-2" type="danger">Minutes: {{
                testet.toFixed(2)
            }}</el-tag>
            <el-tag v-else class="ml-2" type="success">Minutes: {{ testet.toFixed(2) }}</el-tag>
            <el-tag class="ml-2" type="success">Hours Plus Break: {{ testet2.toFixed(2) }}</el-tag>
            <el-tag class="ml-2" type="warning">Hours:  {{ fixar2(testet2)  }}</el-tag>
          </div>
          <div class="input-group input-group-sm mb-3">

          </div>
        </el-card>
        <hr>
      </div>
    </div>
  </div>

  <!-- QUARTA FEIRA  -->

  <div v-show="SickDay[2] === false" class="container">
    <div class="row justify-content-sm-center">
      <div class="col-sm-auto">
        <el-card class="box-card">
          <template #header>
            <div class="card-header">
              <span>Wednesday</span>

            </div>
          </template>
          <div class="demo-range">
            <el-time-picker @change="exibirhorariosMonday(3)" v-model="wednesday" is-range range-separator="To"
              start-placeholder="Start time" end-placeholder="End time" format="HH:mm" size="small" />
          </div>
          <el-checkbox v-model="SegundaC[2]" label="Lock" size="large" />
          <div>
            <div>
              <el-collapse v-model="activeNameW" accordion>
                <el-collapse-item title="Time Off" name="1">
                  <div>
                    <div>In Minutes:</div>
                    <el-input-number v-model="numW" @change="exibirhorariosMonday(3)" :min="0"
                      :max="510"></el-input-number>
                  </div>
                </el-collapse-item>
              </el-collapse>
            </div>
            <el-tag v-if="parseInt(testew) != parseFloat(testew)" class="ml-2" type="danger">Minutes: {{
                testew.toFixed(2)
            }}</el-tag>
            <el-tag v-else class="ml-2" type="success">Minutes: {{ testew.toFixed(2) }}</el-tag>
            <el-tag class="ml-2" type="success">Hours Plus Break: {{ testew2.toFixed(2) }}</el-tag>
            <el-tag class="ml-2" type="warning">Hours:  {{ fixar2(testew2)  }}</el-tag>
          </div>
          <div class="input-group input-group-sm mb-3">

          </div>
        </el-card>
        <hr>
      </div>
    </div>
  </div>

  <!-- Quinta Feira  -->

  <div v-show="SickDay[3] === false" class="container">
    <div class="row justify-content-sm-center">
      <div class="col-sm-auto">
        <el-card class="box-card">
          <template #header>
            <div class="card-header">
              <span>Thursday</span>

            </div>
          </template>
          <div class="demo-range">
            <el-time-picker @change="exibirhorariosMonday(4)" v-model="thursday" is-range range-separator="To"
              start-placeholder="Start time" end-placeholder="End time" format="HH:mm" size="small" />
          </div>
          <el-checkbox v-model="SegundaC[3]" label="Lock" size="large" />
          <div>
            <div>
              <el-collapse v-model="activeNameTT" accordion>
                <el-collapse-item title="Time Off" name="1">
                  <div>
                    <div>In Minutes:</div>
                    <el-input-number v-model="numTT" @change="exibirhorariosMonday(4)" :min="0"
                      :max="510"></el-input-number>
                  </div>
                </el-collapse-item>
              </el-collapse>
            </div>
            <el-tag v-if="parseInt(testett) != parseFloat(testett)" class="ml-2" type="danger">Minutes: {{
                testett.toFixed(2)
            }}</el-tag>
            <el-tag v-else class="ml-2" type="success">Minutes: {{ testett.toFixed(2) }}</el-tag>
            <el-tag class="ml-2" type="success">Hours Plus Break: {{ testett2.toFixed(2) }}</el-tag>
            <el-tag class="ml-2" type="warning">Hours:  {{ fixar2(testett2)  }}</el-tag>
          </div>
          <div class="input-group input-group-sm mb-3">

          </div>
        </el-card>
        <hr>
      </div>
    </div>
  </div>

  <!-- Sexta Feira  -->

  <div v-show="SickDay[4] === false" class="container">
    <div class="row justify-content-sm-center">
      <div class="col-sm-auto">
        <el-card class="box-card">
          <template #header>
            <div class="card-header">
              <span>Friday</span>
            </div>
          </template>
          <div class="demo-range">
            <el-time-picker @change="exibirhorariosMonday(5)" v-model="friday" is-range range-separator="To"
              start-placeholder="Start time" end-placeholder="End time" format="HH:mm" size="small" />
          </div>
          <el-checkbox v-model="SegundaC[4]" label="Lock" size="large" />
          <div>
            <div>
              <el-collapse v-model="activeNameF" accordion>
                <el-collapse-item title="Time Off" name="1">
                  <div>
                    <div>In Minutes:</div>
                    <el-input-number v-model="numF" @change="exibirhorariosMonday(5)" :min="0"
                      :max="510"></el-input-number>
                  </div>
                </el-collapse-item>
              </el-collapse>
            </div>
            <el-tag v-if="parseInt(testef) != parseFloat(testef)" class="ml-2" type="danger">Minutes: {{
                testef.toFixed(2)
            }}</el-tag>
            <el-tag v-else class="ml-2" type="success">Minutes: {{ testef.toFixed(2) }}</el-tag>
            <el-tag class="ml-2" type="success">Hours Plus Break: {{ testef2.toFixed(2) }}</el-tag>
            <el-tag class="ml-2" type="warning">Hours:  {{ fixar2(testef2)  }}</el-tag>
          </div>
          <div class="input-group input-group-sm mb-3">
          </div>
        </el-card>
        <hr>
      </div>
    </div>
    Made with ❤️ by Augusto Zeilmann - 2022 
    
  </div>


  
  <el-dialog
    v-model="dialogVisible"
    title="Message"
    width="50%"
    :before-close="handleClose"
  >
    <span>Week Hours</span>
    <template #footer>
      <el-table
    :data="tableData"
    style="width: 100%"
    :row-class-name="tableRowClassName"
  >
    <el-table-column prop="date" label="Day" width="180" />
    <el-table-column prop="in" label="In"  />
    <el-table-column prop="out" label="Out" />
    <el-table-column prop="hours" label="Hours" />
  </el-table>
       
        
        
        <el-button type="primary" @click="dialogVisible = false">
          Confirm
        </el-button>
      
    </template>
  </el-dialog>

</template>
  
<script>
import moment from 'moment'


export default {
  data() {
    return {
      activeName: ['0'],
      activeNameT: ['0'],
      activeNameW: ['0'],
      activeNameTT: ['0'],
      activeNameF: ['0'],
      numM: 0,
      numT: 0,
      numW: 0,
      numTT: 0,
      numF: 0,
      monday: [new Date(2022, 9, 7, 7, 30), new Date(2022, 9, 7, 16, 0)],
      tuesday: [new Date(2022, 9, 7, 7, 30), new Date(2022, 9, 7, 16, 0)],
      wednesday: [new Date(2022, 9, 7, 7, 30), new Date(2022, 9, 7, 16, 0)],
      thursday: [new Date(2022, 9, 7, 7, 30), new Date(2022, 9, 7, 16, 0)],
      friday: [new Date(2022, 9, 7, 7, 30), new Date(2022, 9, 7, 16, 0)],
      count: 1,
      SegundaC: [false, false, false, false, false],
      SickDay: [false, false, false, false, false],
      Seletor: [false, false, false, false, false],
      testem: 510,
      testem2: 8.5,
      testet: 510,
      testet2: 8.5,
      testew: 510,
      testew2: 8.5,
      testett: 510,
      testett2: 8.5,
      testef: 510,
      testef2: 8.5,
      totalh: 42.5,
      totalB: 37.5,
      totalTopM: 0,
      totalTopM1: 0,
      valorrec1: 5,
      totalC: 42.5,
      dialogVisible: false,
      JuncSegunda_1 : "00:00",
      JuncSegunda_2 : "00:00",
      JuncTerca_1 : "00:00",
      JuncTerca_2 : "00:00",
      JuncQuarta_1 : "00:00",
      JuncQuarta_2 : "00:00",
      JuncQuinta_1 : "00:00",
      JuncQuinta_2 : "00:00",
      JuncSexta_1 : "00:00",
      JuncSexta_2 : "00:00",
      tableData:  [{
          date: 'Monday',
          in: '07:30',
          out: '16:00',
          hours: '8.5'
        }, {
          date: 'Tuesday',
          in: '07:30',
          out: '16:00',
          hours: '8.5'
        }, {
          date: 'Wednesday',
          in: '07:30',
          out: '16:00',
          hours: '8.5'
        }, {
          date: 'Wednesday',
          in: '07:30',
          out: '16:00',
          hours: '8.5'
        }, {
          date: 'Friday',
          in: '07:30',
          out: '16:00',
          hours: '8.5'
        }, {
          date: '',
          in: '',
          out: '',
          hours: '8.5'
        }]

      

    };
  },

  methods: {

    fixar2(paramsteste){
      paramsteste = paramsteste -1
      return paramsteste.toFixed(2)
    },


    tableRowClassName({row}) {
      console.log(row.date)
        if (row.in === "Holidays/Sick") {
          return 'warning-row'
        } else  {
          return 'success-row'
        }

        
        
      },

    listahorarios(){

      

      this.dialogVisible = true
       //MONDAY
       if (this.SickDay[0] === true) {
        this.JuncSegunda_1 = "Holidays/Sick"
        this.JuncSegunda_2 = "Holidays/Sick"
        this.tableData[0].in = this.JuncSegunda_1
        this.tableData[0].out = this.JuncSegunda_2
        this.tableData[0].hours = "0.00"
       }else{

        var Segunda_list_1 = moment(this.monday[0]);
        let horaSegunda1_l = moment(Segunda_list_1).format('H');
        let minutoSegunda1_l= moment(Segunda_list_1).format('m');
        horaSegunda1_l = this.funcaoColocaZero(horaSegunda1_l)
        minutoSegunda1_l = this.funcaoColocaZero(minutoSegunda1_l)

        this.JuncSegunda_1 = horaSegunda1_l + ":" + minutoSegunda1_l
      

        var Segunda_list_2 = moment(this.monday[1]);
        let horaSegunda2_l = moment(Segunda_list_2).format('H');
        let minutoSegunda2_l = moment(Segunda_list_2).format('m');
        horaSegunda2_l = this.funcaoColocaZero(horaSegunda2_l)
        minutoSegunda2_l = this.funcaoColocaZero(minutoSegunda2_l)
        
        this.JuncSegunda_2 = horaSegunda2_l + ":" + minutoSegunda2_l

        this.tableData[0].in = this.JuncSegunda_1
        this.tableData[0].out = this.JuncSegunda_2
        let mm = this.testem2.toFixed(2)- 1
        this.tableData[0].hours = mm.toFixed(2)
        
      }
       
        //TERCA
        if (this.SickDay[1] === true) {
        this.JuncTerca_1 = "Holidays/Sick"
        this.JuncTerca_2 = "Holidays/Sick"
        this.tableData[1].in = this.JuncTerca_1
        this.tableData[1].out = this.JuncTerca_2
        this.tableData[1].hours = "0.00"
       }else{
        var Terca_list_1 = moment(this.tuesday[0]);
        let horaTerca1_l = moment(Terca_list_1).format('H');
        let minutoTerca1_l= moment(Terca_list_1).format('m');
        horaTerca1_l = this.funcaoColocaZero(horaTerca1_l)
        minutoTerca1_l = this.funcaoColocaZero(minutoTerca1_l)

       this.JuncTerca_1 = horaTerca1_l + ":" + minutoTerca1_l
      

        var Terca_list_2 = moment(this.tuesday[1]);
        let horaTerca2_l = moment(Terca_list_2).format('H');
        let minutoTerca2_l= moment(Terca_list_2).format('m');
        horaTerca2_l = this.funcaoColocaZero(horaTerca2_l)
        minutoTerca2_l = this.funcaoColocaZero(minutoTerca2_l)
        
        this.JuncTerca_2 = horaTerca2_l + ":" + minutoTerca2_l
        this.tableData[1].in = this.JuncTerca_1
        this.tableData[1].out = this.JuncTerca_2
        let ttu = this.testet2.toFixed(2)- 1
        this.tableData[1].hours = ttu.toFixed(2)
       }

        // QUARTA

        if (this.SickDay[2] === true) {
        this.JuncQuarta_1 = "Holidays/Sick"
        this.JuncQuarta_2 = "Holidays/Sick"
        this.tableData[2].in = this.JuncQuarta_1
        this.tableData[2].out = this.JuncQuarta_2
        this.tableData[2].hours = "0.00"
       }else{
        
        var Quarta_list_1 = moment(this.wednesday[0]);
        let horaQuarta1_l = moment(Quarta_list_1).format('H');
        let minutoQuarta1_l= moment(Quarta_list_1).format('m');
        horaQuarta1_l = this.funcaoColocaZero(horaQuarta1_l)
        minutoQuarta1_l = this.funcaoColocaZero(minutoQuarta1_l)

       this.JuncQuarta_1 = horaQuarta1_l + ":" + minutoQuarta1_l
      

        var Quarta_list_2 = moment(this.wednesday[1]);
        let horaQuarta2_l = moment(Quarta_list_2).format('H');
        let minutoQuarta2_l= moment(Quarta_list_2).format('m');
        horaQuarta2_l = this.funcaoColocaZero(horaQuarta2_l)
        minutoQuarta2_l = this.funcaoColocaZero(minutoQuarta2_l)
        
        this.JuncQuarta_2 = horaQuarta2_l + ":" + minutoQuarta2_l
        this.tableData[2].in = this.JuncQuarta_1
        this.tableData[2].out = this.JuncQuarta_2
        let ww = this.testew2.toFixed(2)- 1
        this.tableData[2].hours = ww.toFixed(2)
       }
        
        //QUINTA

        if (this.SickDay[3] === true) {
        this.JuncQuinta_1 = "Holidays/Sick"
        this.JuncQuinta_2 = "Holidays/Sick"
        this.tableData[3].in = this.JuncQuinta_1
        this.tableData[3].out = this.JuncQuinta_2
        this.tableData[3].hours = "0.00"
       }else{
        
        var Quinta_list_1 = moment(this.thursday[0]);
        let horaQuinta1_l = moment(Quinta_list_1).format('H');
        let minutoQuinta1_l= moment(Quinta_list_1).format('m');
        horaQuinta1_l = this.funcaoColocaZero(horaQuinta1_l)
        minutoQuinta1_l = this.funcaoColocaZero(minutoQuinta1_l)

       this.JuncQuinta_1 = horaQuinta1_l + ":" + minutoQuinta1_l
      

        var Quinta_list_2 = moment(this.thursday[1]);
        let horaQuinta2_l = moment(Quinta_list_2).format('H');
        let minutoQuinta2_l= moment(Quinta_list_2).format('m');
        horaQuinta2_l = this.funcaoColocaZero(horaQuinta2_l)
        minutoQuinta2_l = this.funcaoColocaZero(minutoQuinta2_l)
        
        this.JuncQuinta_2 = horaQuinta2_l + ":" + minutoQuinta2_l
        this.tableData[3].in = this.JuncQuinta_1
        this.tableData[3].out = this.JuncQuinta_2
        let tth = this.testett2.toFixed(2)- 1
        this.tableData[3].hours = tth.toFixed(2)
       }

        //SEXTA

        if (this.SickDay[4] === true) {
        this.JuncSexta_1 = "Holidays/Sick"
        this.JuncSexta_2 = "Holidays/Sick"
        this.tableData[4].in = this.JuncSexta_1
        this.tableData[4].out = this.JuncSexta_2
        this.tableData[4].hours = "0.00"
       }else{
        
        var Sexta_list_1 = moment(this.friday[0]);
        let horaSexta1_l = moment(Sexta_list_1).format('H');
        let minutoSexta1_l= moment(Sexta_list_1).format('m');
        horaSexta1_l = this.funcaoColocaZero(horaSexta1_l)
        minutoSexta1_l = this.funcaoColocaZero(minutoSexta1_l)

       this.JuncSexta_1 = horaSexta1_l + ":" + minutoSexta1_l
      

        var Sexta_list_2 = moment(this.friday[1]);
        let horaSexta2_l = moment(Sexta_list_2).format('H');
        let minutoSexta2_l= moment(Sexta_list_2).format('m');
        horaSexta2_l = this.funcaoColocaZero(horaSexta2_l)
        minutoSexta2_l = this.funcaoColocaZero(minutoSexta2_l)
        
        this.JuncSexta_2 = horaSexta2_l + ":" + minutoSexta2_l
        this.tableData[4].in = this.JuncSexta_1
        this.tableData[4].out = this.JuncSexta_2
        let fr = this.testef2.toFixed(2)- 1
        this.tableData[4].hours = fr.toFixed(2)
       }

       if (this.totalB.toFixed(2) === '0.00' || this.totalB.toFixed(2) === '37.50' || this.totalB.toFixed(2) === '22.50' || this.totalB.toFixed(2) === '30.00' || this.totalB.toFixed(2) === '15.00' || this.totalB.toFixed(2) === '7.50'){
        this.tableData[5].hours = this.totalB.toFixed(2) + " 😍"
       }else{
        this.tableData[5].hours = this.totalB.toFixed(2) + " 😭"
       }

       
    },

    funcaoColocaZero(paramsCzero){
      if (paramsCzero.length === 1){
        
        return paramsCzero = "0" + paramsCzero

      }else{
        return paramsCzero
      }
    },


    exibirhorariosMonday(params) {



      if (params === 1) {
        this.SegundaC[0] = true

      }
      if (params === 2) {
        this.SegundaC[1] = true
      }
      if (params === 3) {
        this.SegundaC[2] = true
      }
      if (params === 4) {
        this.SegundaC[3] = true
      }
      if (params === 5) {
        this.SegundaC[4] = true
      }



      var aM = moment(this.monday[1]);
      var bM = moment(this.monday[0]);
      this.testem = (aM.diff(bM, 'minutes'))
      this.testem2 = this.testem / 60;
      if (this.activeName[0] === '1') {
        this.testem = this.testem - this.numM
        this.testem2 = this.testem / 60;
      }

      var aT = moment(this.tuesday[1]);
      var bT = moment(this.tuesday[0]);
      this.testet = (aT.diff(bT, 'minutes'))
      this.testet2 = this.testet / 60;
      if (this.activeNameT[0] === '1') {
        this.testet = this.testet - this.numT
        this.testet2 = this.testet / 60;
      }

      var aW = moment(this.wednesday[1]);
      var bW = moment(this.wednesday[0]);
      this.testew = (aW.diff(bW, 'minutes'))
      this.testew2 = this.testew / 60;
      if (this.activeNameW[0] === '1') {
        this.testew = this.testew - this.numW
        this.testew2 = this.testew / 60;
      }

      var aTT = moment(this.thursday[1]);
      var bTT = moment(this.thursday[0]);
      this.testett = (aTT.diff(bTT, 'minutes'))
      this.testett2 = this.testett / 60;
      if (this.activeNameTT[0] === '1') {
        this.testett = this.testett - this.numTT
        this.testett2 = this.testett / 60;
      }

      var aF = moment(this.friday[1]);
      var bF = moment(this.friday[0]);
      this.testef = (aF.diff(bF, 'minutes'))
      this.testef2 = this.testef / 60;
      if (this.activeNameF[0] === '1') {
        this.testef = this.testef - this.numF
        this.testef2 = this.testef / 60;
      }


      this.totalh = this.testem2 + this.testet2 + this.testew2 + this.testett2 + this.testef2
      let totalTopM = this.testem + this.testet + this.testew + this.testett + this.testef

      let totalTop = this.totalC - this.totalh
      let totalM = 2550 - totalTopM


      

      if (this.valorrec1 === 1){
        this.totalB = 7.5
        this.totalC = 12.5
      }
      if (this.valorrec1 === 2){
        this.totalB = 15
        this.totalC = 20
      }
      if (this.valorrec1 === 3){
        this.totalB = 22.5
        this.totalC = 27.5
      }
      if (this.valorrec1 === 4){
        this.totalB = 30
        this.totalC = 35
      }
      if (this.valorrec1 === 5){
        this.totalB = 37.5
        this.totalC = 42.5
      }

      if (this.SickDay[0] === true){
        this.testem2 = 0;
        this.SegundaC[0] = true;
      }
      if (this.SickDay[1] === true){
        this.testet2 = 0;
        this.SegundaC[1] = true;
      }
      if (this.SickDay[2] === true){
        this.testew2 = 0;
        this.SegundaC[2] = true;
      }
      if (this.SickDay[3] === true){
        this.testett2 = 0;
        this.SegundaC[3] = true;
      }
      if (this.SickDay[4] === true){
        this.testef2 = 0;
        this.SegundaC[4] = true;
      }

      if (this.SickDay[0] === true || this.SegundaC[0] === true ){
        this.Seletor[0] = true 
       // alert(this.Seletor[0])
      }else{
        this.Seletor[0] = false
      }

      if (this.SickDay[1] === true || this.SegundaC[1] === true ){
        this.Seletor[1] = true 
      }else{
        this.Seletor[1] = false
      }

      if (this.SickDay[2] === true || this.SegundaC[2] === true ){
        this.Seletor[2] = true 
      }else{
        this.Seletor[2] = false
      }

      if (this.SickDay[3] === true || this.SegundaC[3] === true ){
        this.Seletor[3] = true 
      }else{
        this.Seletor[3] = false
      }

      if (this.SickDay[4] === true || this.SegundaC[4] === true ){
        this.Seletor[4] = true 
      }else{
        this.Seletor[4] = false
      }

      
      let valorrec = this.SegundaC.filter((value) => value === false).length;
      this.valorrec1 = this.SickDay.filter((value) => value === false).length;
      
      valorrec = Math.min(valorrec, this.valorrec1)
 
      //alert(valorrec)
      let divisaoS = totalM / valorrec
      let divisaoS1 = divisaoS / 60
      //MUDAR SEGUNDA FEIRA

      if (this.Seletor[0] === false) {
       //alert("entrou segunda")
        var aM1 = moment(this.monday[1]);
        let addHoraSegunda = moment(aM1).add(divisaoS, 'm');
        let horaSegunda1 = moment(addHoraSegunda).format('H');
        let minutoSegunda1 = moment(addHoraSegunda).format('m');
        this.monday[1] = new Date(2022, 9, 7, horaSegunda1, minutoSegunda1)
        this.testem2 = this.testem2 + divisaoS1;
        this.testem = this.testem + divisaoS;
      }

   
      //MUDAR TERCA FEIRA

      if (this.Seletor[1] === false) {
       // alert("entrou Terca")
        var aT1 = moment(this.tuesday[1]);
        let addHoraTerca = moment(aT1).add(divisaoS, 'm');
        let horaTerca1 = moment(addHoraTerca).format('H');
        let minutoTerca1 = moment(addHoraTerca).format('m');
        this.tuesday[1] = new Date(2022, 9, 7, horaTerca1, minutoTerca1)


        this.testet2 = this.testet2 + divisaoS1;
        this.testet = this.testet + divisaoS;




      }

      //MUDAR QUARTA FEIRA
      if (this.Seletor[2] === false) {
        var aW1 = moment(this.wednesday[1]);
        let addHoraQuarta = moment(aW1).add(divisaoS, 'm');
        let horaQuarta1 = moment(addHoraQuarta).format('H');
        let minutoQuarta1 = moment(addHoraQuarta).format('m');
        this.wednesday[1] = new Date(2022, 9, 7, horaQuarta1, minutoQuarta1),

          this.testew2 = this.testew2 + divisaoS1
        this.testew = this.testew + divisaoS


      }

      //MUDAR QUINTA FEIRA
      if (this.Seletor[3] === false) {
        var aTT1 = moment(this.thursday[1]);
        let addHoraQuinta = moment(aTT1).add(divisaoS, 'm');
        let horaQuinta1 = moment(addHoraQuinta).format('H');
        let minutoQuinta1 = moment(addHoraQuinta).format('m');
        this.thursday[1] = new Date(2022, 9, 7, horaQuinta1, minutoQuinta1),

          this.testett2 = this.testett2 + divisaoS1
        this.testett = this.testett + divisaoS
      }

      //MUDAR SEXTA FEIRA

      if (this.Seletor[4] === false) {
        var aF1 = moment(this.friday[1]);
        let addHoraSexta = moment(aF1).add(divisaoS, 'm');
        let horaSexta1 = moment(addHoraSexta).format('H');
        let minutoSexta1 = moment(addHoraSexta).format('m');
        this.friday[1] = new Date(2022, 9, 7, horaSexta1, minutoSexta1),

        this.testef2 = this.testef2 + divisaoS1
        this.testef = this.testef + divisaoS

        //this.totalh = this.testem2 + this.testet2 + this.testew2 + this.testett2 + this.testef2
        //let totalTopM = this.testem + this.testet + this.testew + this.testett + this.testef

      }



      
      this.totalh = this.testem2 + this.testet2 + this.testew2 + this.testett2 + this.testef2

      console.log("Segunda: " + this.testem2 + " Terca: " + this.testet2 + " Quarta: " + this.testew2 + " Quinta: " + this.testett2 + " Sexta: " + this.testef2)

      this.totalTopM1 = this.testem + this.testet + this.testew + this.testett + this.testef

      this.totalTopM1 = 2550 - this.totalTopM1

      totalTop = this.totalC - this.totalh
      console.log(totalTop);
      totalM = 2550 - totalTopM
      this.totalB = this.totalh - this.valorrec1
      

      if (parseInt(this.testem) != parseFloat(this.testem) || parseInt(this.testet) != parseFloat(this.testet) || parseInt(this.testew) != parseFloat(this.testew) || parseInt(this.testett) != parseFloat(this.testett) || parseInt(this.testef) != parseFloat(this.testef)) {
        this.$message({
          message: 'You need to add minutes until everything turns green!',
          type: 'warning',
          duration: 2000
        });

      }

      


    }

  }

};





</script>
  
<style>
.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.text {
  font-size: 14px;
}

.item {
  margin-bottom: 18px;
}

.box-card {
  width: 420px;
}

.card-body {

  padding: 2px;
  border-style: dotted;
}

.demo-range .el-range-separator {
  box-sizing: content-box;
}

span {
  font-size: 12px;
}

.el-checkbox {
  font-size: 12px;

}

.el-table .warning-row {
    background: rgb(253, 161, 161);
    color:#000000
  }

  .el-table .success-row {
    background: #f0f9eb;
  }
</style>