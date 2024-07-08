<template>
  <div class="container">
    <table>
      <thead>
        <tr>
          <th colspan="7">без испытательного пальца</th>
          <th colspan="4">С испытательным пальцем</th>
          <th colspan="4">SpO2 = 70%, Perf = 1%(-15 дБ)</th>
          <th colspan="4">SpO2 = 98%(95%), Perf = 1%(-15 дБ)</th>
          <th colspan="4">SpO2 = 98%(95%), Perf = 20%(0 дБ)</th>
          <th colspan="4">SpO2 = 70%, Perf = 20%(0 дБ)</th>
          <th colspan="2"></th>
        </tr>
        <tr>
          <th rowspan="2">№</th>
          <th rowspan="2">Pin7 DA4, B</th>
          <th rowspan="2">R65, B</th>
          <th rowspan="2">Direct</th>
          <th rowspan="2">Amplif</th>
          <th colspan="2">DACA</th>
          <th rowspan="2">Pin1 DA4, B</th>
          <th rowspan="2">Pin8 DA4, B</th>
          <th rowspan="2">Pin7 DA4, B</th>
          <th rowspan="2">R65, B</th>
          <th rowspan="2">15</th>
          <th rowspan="2">120</th>
          <th rowspan="2">240</th>
          <th rowspan="2">350</th>
          <th rowspan="2">15</th>
          <th rowspan="2">120</th>
          <th rowspan="2">240</th>
          <th rowspan="2">350</th>
          <th rowspan="2">15</th>
          <th rowspan="2">120</th>
          <th rowspan="2">240</th>
          <th rowspan="2">350</th>
          <th rowspan="2">15</th>
          <th rowspan="2">120</th>
          <th rowspan="2">240</th>
          <th rowspan="2">350</th>
          <th rowspan="2">Вывод</th>
          <th rowspan="2">Исполнитель</th>
        </tr>
        <tr>
          <th>Без преграды</th>
          <th>С преградой</th>
        </tr>
      </thead>
      <tbody>
        <template v-for="(row, index) in rows" :key="index">
          <tr>
            <td :rowspan="2">{{ index + 1 }}</td>
            <td><textarea v-model="row.pin7DA4_1" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td><textarea v-model="row.r65B_1" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td>
              <select v-model="row.direct_1" @keydown.enter.prevent="focusNext($event)">
                <option value="Соотв.">Соотв.</option>
                <option value="Несоотв.">Несоотв.</option>
              </select>
            </td>
            <td>
              <select v-model="row.amplif_1" @keydown.enter.prevent="focusNext($event)">
                <option value="Соотв.">Соотв.</option>
                <option value="Несоотв.">Несоотв.</option>
              </select>
            </td>
            <td>
              <select v-model.number="row.dacaNoObstacle_1" @keydown.enter.prevent="focusNext($event)">
                <option value="Соотв.">Соотв.</option>
                <option value="Несоотв.">Несоотв.</option>
              </select>
            </td>
            <td>
              <select v-model.number="row.dacaWithObstacle_1" @keydown.enter.prevent="focusNext($event)">
                <option value="Соотв.">Соотв.</option>
                <option value="Несоотв.">Несоотв.</option>
              </select>
            </td>
            <td><textarea v-model="row.pin1DA4_1" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td><textarea v-model="row.pin8DA4_1" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td><textarea v-model="row.pin7DA4_2_1" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td><textarea v-model="row.r65B_2_1" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td :rowspan="2"><textarea v-model="row.spo2_15_1" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td :rowspan="2"><textarea v-model="row.spo2_120_1" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td :rowspan="2"><textarea v-model="row.spo2_240_1" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td :rowspan="2"><textarea v-model="row.spo2_350_1" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td :rowspan="2"><textarea v-model="row.spo2_15_2" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td :rowspan="2"><textarea v-model="row.spo2_120_2" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td :rowspan="2"><textarea v-model="row.spo2_240_2" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td :rowspan="2"><textarea v-model="row.spo2_350_2" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td :rowspan="2"><textarea v-model="row.spo2_15_3" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td :rowspan="2"><textarea v-model="row.spo2_120_3" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td :rowspan="2"><textarea v-model="row.spo2_240_3" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td :rowspan="2"><textarea v-model="row.spo2_350_3" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td :rowspan="2"><textarea v-model="row.spo2_15_4" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td :rowspan="2"><textarea v-model="row.spo2_120_4" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td :rowspan="2"><textarea v-model="row.spo2_240_4" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td :rowspan="2"><textarea v-model="row.spo2_350_4" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td :rowspan="2">
              <textarea class="wide" v-model="row.conclusion" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea>
            </td>
            <td :rowspan="2">
              <textarea class="wide" v-model="row.performer" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea>
            </td>
          </tr>
          <tr>
            <td><textarea v-model="row.pin7DA4_2" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td><textarea v-model="row.r65B_2" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td>
              <select v-model="row.direct_2" @keydown.enter.prevent="focusNext($event)">
                <option value="Соотв.">Соотв.</option>
                <option value="Несоотв.">Несоотв.</option>
              </select>
            </td>
            <td>
              <select v-model="row.amplif_2" @keydown.enter.prevent="focusNext($event)">
                <option value="Соотв.">Соотв.</option>
                <option value="Несоотв.">Несоотв.</option>
              </select>
            </td>
            <td>
              <select v-model.number="row.dacaNoObstacle_2" @keydown.enter.prevent="focusNext($event)">
                <option value="Соотв.">Соотв.</option>
                <option value="Несоотв.">Несоотв.</option>
              </select>
            </td>
            <td>
              <select v-model.number="row.dacaWithObstacle_2" @keydown.enter.prevent="focusNext($event)">
                <option value="Соотв.">Соотв.</option>
                <option value="Несоотв.">Несоотв.</option>
              </select>
            </td>
            <td><textarea v-model="row.pin1DA4_2" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td><textarea v-model="row.pin8DA4_2" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td><textarea v-model="row.pin7DA4_2_2" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
            <td><textarea v-model="row.r65B_2_2" @input="adjustSize" @keydown.enter.prevent="focusNext($event)"></textarea></td>
          </tr>
        </template>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      rows: [
        {
          pin7DA4_1: '',
          r65B_1: '',
          direct_1: '',
          amplif_1: '',
          dacaNoObstacle_1: '',
          dacaWithObstacle_1: '',
          pin1DA4_1: '',
          pin8DA4_1: '',
          pin7DA4_2_1: '',
          r65B_2_1: '',
          pin7DA4_2: '',
          r65B_2: '',
          direct_2: '',
          amplif_2: '',
          dacaNoObstacle_2: '',
          dacaWithObstacle_2: '',
          pin1DA4_2: '',
          pin8DA4_2: '',
          pin7DA4_2_2: '',
          r65B_2_2: '',
          spo2_15_1: '',
          spo2_120_1: '',
          spo2_240_1: '',
          spo2_350_1: '',
          spo2_15_2: '',
          spo2_120_2: '',
          spo2_240_2: '',
          spo2_350_2: '',
          spo2_15_3: '',
          spo2_120_3: '',
          spo2_240_3: '',
          spo2_350_3: '',
          spo2_15_4: '',
          spo2_120_4: '',
          spo2_240_4: '',
          spo2_350_4: '',
          conclusion: '',
          performer: '',
        },
        {
          pin7DA4_1: '',
          r65B_1: '',
          direct_1: '',
          amplif_1: '',
          dacaNoObstacle_1: '',
          dacaWithObstacle_1: '',
          pin1DA4_1: '',
          pin8DA4_1: '',
          pin7DA4_2_1: '',
          r65B_2_1: '',
          pin7DA4_2: '',
          r65B_2: '',
          direct_2: '',
          amplif_2: '',
          dacaNoObstacle_2: '',
          dacaWithObstacle_2: '',
          pin1DA4_2: '',
          pin8DA4_2: '',
          pin7DA4_2_2: '',
          r65B_2_2: '',
          spo2_15_1: '',
          spo2_120_1: '',
          spo2_240_1: '',
          spo2_350_1: '',
          spo2_15_2: '',
          spo2_120_2: '',
          spo2_240_2: '',
          spo2_350_2: '',
          spo2_15_3: '',
          spo2_120_3: '',
          spo2_240_3: '',
          spo2_350_3: '',
          spo2_15_4: '',
          spo2_120_4: '',
          spo2_240_4: '',
          spo2_350_4: '',
          conclusion: '',
          performer: '',
        },
        {
          pin7DA4_1: '',
          r65B_1: '',
          direct_1: '',
          amplif_1: '',
          dacaNoObstacle_1: '',
          dacaWithObstacle_1: '',
          pin1DA4_1: '',
          pin8DA4_1: '',
          pin7DA4_2_1: '',
          r65B_2_1: '',
          pin7DA4_2: '',
          r65B_2: '',
          direct_2: '',
          amplif_2: '',
          dacaNoObstacle_2: '',
          dacaWithObstacle_2: '',
          pin1DA4_2: '',
          pin8DA4_2: '',
          pin7DA4_2_2: '',
          r65B_2_2: '',
          spo2_15_1: '',
          spo2_120_1: '',
          spo2_240_1: '',
          spo2_350_1: '',
          spo2_15_2: '',
          spo2_120_2: '',
          spo2_240_2: '',
          spo2_350_2: '',
          spo2_15_3: '',
          spo2_120_3: '',
          spo2_240_3: '',
          spo2_350_3: '',
          spo2_15_4: '',
          spo2_120_4: '',
          spo2_240_4: '',
          spo2_350_4: '',
          conclusion: '',
          performer: '',
        },
      ],
    };
  },
  methods: {
    handleKeyDown(event) {
      if (event.key === 'Enter' || event.key === 'Tab') {
        event.preventDefault();
        this.focusNext(event);
      }
    },
    focusNext(event) {
      const currentInput = event.target;
      const inputs = Array.from(document.querySelectorAll('textarea, select'));
      const currentIndex = inputs.indexOf(currentInput);
      const nextInput = inputs[currentIndex + 1];
      if (nextInput) {
        nextInput.focus();
      }
    },
    adjustSize(event) {
      const textarea = event.target;
      textarea.style.height = 'auto';
      textarea.style.height = textarea.scrollHeight + 'px';
    },
  },
};
</script>

<style scoped>
.container{
  width: 1440px;
}
table {
  width: 100%;
  border-collapse: collapse;
}
th, td {
  border: 1px solid #000;
  padding: 5px;
  text-align: center;
}
textarea {
  min-width: 50px;
  width: 100%;
  border: none;
  text-align: center;
  padding: 5px;
  box-sizing: border-box;  
  resize: none;  
  overflow-y: hidden;
}
textarea:focus {
  outline: none;
  background-color: #f0f0f0;
}
textarea.wide {
  min-width: 100px;
}
select {
  width: 60px;
  box-sizing: border-box;
}
</style>