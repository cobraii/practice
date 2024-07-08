<template>
  <div class="container">
    <table>
      <thead>
        <tr>
          <th colspan="12"></th>
          <th colspan="5">Клавиатура</th>
          <th colspan="11">Проверка работы от АКБ, переключения питания, работы зарядного устройства</th>
          <th colspan="4">С подключённым датчиком SpO<sub>2</sub></th>
        </tr>
        <tr>
          <th rowspan="3">№</th>
          <th rowspan="3">Дата</th>
          <th rowspan="3">Контр. сумма</th>
          <th rowspan="3">КЗ</th>
          <th rowspan="3">U<sub>пит</sub>, В</th>
          <th rowspan="3">C35, В</th>
          <th rowspan="3">Pin7 MK U<sub>ref</sub></th>
          <th rowspan="3">U<sub>пит</sub>, В</th>
          <th rowspan="3">C41, В</th>
          <th rowspan="3">C14, В</th>
          <th rowspan="3">C1, В</th>
          <th rowspan="3">C45, В</th>
          <th rowspan="3">△</th>
          <th rowspan="3">▽</th>
          <th rowspan="3">SpO 2</th>
          <th rowspan="3">Pr</th>
          <th rowspan="3">△</th>
          <th rowspan="3">AKБ</th>
          <th rowspan="3">Pin61 MK</th>
          <th colspan="2">C35</th>
          <th rowspan="3">VD 25</th>
          <th rowspan="3">VB AT, R92</th>
          <th colspan="2">Pin60 MK</th>
          <th rowspan="3">VD 29</th>
          <th rowspan="3">Inot, мА</th>
          <th rowspan="3">R66, R68, R70, R72</th>
          <th colspan="2">I светодиода, мА</th>
          <th rowspan="3">Pin1 DA4, В</th>
          <th rowspan="3">Pin8 DA4, В</th>
        </tr>
        <tr>
          <th>акб</th>
          <th>ИП</th>
          <th>акб</th>
          <th>ИП</th>
          <th>Без преграды</th>
          <th>С преградой</th>
        </tr>
      </thead>
      <tbody>
        <template v-for="(row, index) in rows" :key="index">
          <tr>
            <td :rowspan="2">{{ index + 1 }}</td>
            <td :rowspan="2"><textarea class="wide"v-model="row.date" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td :rowspan="2"><textarea v-model="row.controlSum" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td :rowspan="2"><textarea v-model="row.k3" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td :rowspan="2"><textarea v-model="row.pit" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td :rowspan="2"><textarea v-model="row.c35" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td :rowspan="2"><textarea v-model="row.pin7MK" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.Upit" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.c41" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.c14" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.c1" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.c45" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.triangle" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.downTriangle" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.spO2" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.pr" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.triangleA" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.akb" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.pin61MK" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td>
              <select v-model="row.c35Akb" @input="autoResize" @keydown="handleKeyDown">
                <option value="Соотв.">Соотв.</option>
                <option value="Несоотв.">Несоотв.</option>
              </select>
            </td>
            <td>
              <select v-model="row.c35Ip" @input="autoResize" @keydown="handleKeyDown">
                <option value="Соотв.">Соотв.</option>
                <option value="Несоотв.">Несоотв.</option>
              </select>
            </td>
            <td><textarea v-model="row.vd25" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.vbAT" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td>
              <select v-model="row.pin60MKAkb" @input="autoResize" @keydown="handleKeyDown">
                <option value="Соотв.">Соотв.</option>
                <option value="Несоотв.">Несоотв.</option>
              </select>
            </td>
            <td>
              <select v-model="row.pin60MKIp" @input="autoResize" @keydown="handleKeyDown">
                <option value="Соотв.">Соотв.</option>
                <option value="Несоотв.">Несоотв.</option>
              </select>
            </td>
            <td><textarea v-model="row.vd29" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.inotMA" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.r66" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td>
              <select v-model="row.lNoObstacle" @input="autoResize" @keydown="handleKeyDown">
                <option value="Соотв.">Соотв.</option>
                <option value="Несоотв.">Несоотв.</option>
              </select>
            </td>
            <td>
              <select v-model="row.lWithObstacle" @input="autoResize" @keydown="handleKeyDown">
                <option value="Соотв.">Соотв.</option>
                <option value="Несоотв.">Несоотв.</option>
              </select>
            </td>
            <td><textarea v-model="row.pin1DA4" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.pin8DA4" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
          </tr>
          <tr>
            <td><textarea v-model="row.Upit2" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.c412" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.c142" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.c12" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.c452" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.triangle2" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.downTriangle2" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.spO22" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.pr2" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.triangleA2" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.akb2" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.pin61MK2" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td>
              <select v-model="row.c35Akb2" @input="autoResize" @keydown="handleKeyDown">
                <option value="Соотв.">Соотв.</option>
                <option value="Несоотв.">Несоотв.</option>
              </select>
            </td>
            <td>
              <select v-model="row.c35Ip2" @input="autoResize" @keydown="handleKeyDown">
                <option value="Соотв.">Соотв.</option>
                <option value="Несоотв.">Несоотв.</option>
              </select>
            </td>
            <td><textarea v-model="row.vd252" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.vbAT2" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td>
              <select v-model="row.pin60MKAkb2" @input="autoResize" @keydown="handleKeyDown">
                <option value="Соотв.">Соотв.</option>
                <option value="Несоотв.">Несоотв.</option>
              </select>
            </td>
            <td>
              <select v-model="row.pin60MKIp2" @input="autoResize" @keydown="handleKeyDown">
                <option value="Соотв.">Соотв.</option>
                <option value="Несоотв.">Несоотв.</option>
              </select>
            </td>
            <td><textarea v-model="row.vd292" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.inotMA2" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.r662" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td>
              <select v-model="row.lNoObstacle2" @input="autoResize" @keydown="handleKeyDown">
                <option value="Соотв.">Соотв.</option>
                <option value="Несоотв.">Несоотв.</option>
              </select>
            </td>
            <td>
              <select v-model="row.lWithObstacle2" @input="autoResize" @keydown="handleKeyDown">
                <option value="Соотв.">Соотв.</option>
                <option value="Несоотв.">Несоотв.</option>
              </select>
            </td>
            <td><textarea v-model="row.pin1DA42" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
            <td><textarea v-model="row.pin8DA42" @input="autoResize" @keydown="handleKeyDown"></textarea></td>
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
          date: '',
          controlSum: '',
          k3: '',
          pit: '',
          c35: '',
          pin7MK: '',
          Upit: '',
          c41: '',
          c14: '',
          c1: '',
          c45: '',
          triangle: '',
          downTriangle: '',
          spO2: '',
          pr: '',
          triangleA: '',
          akb: '',
          pin61MK: '',
          c35Akb: '',
          c35Ip: '',
          vd25: '',
          vbAT: '',
          pin60MKAkb: '',
          pin60MKIp: '',
          vd29: '',
          inotMA: '',
          r66: '',
          lNoObstacle: '',
          lWithObstacle: '',
          pin1DA4: '',
          pin8DA4: '',
          triangle2: '',
          downTriangle2: '',
          spO22: '',
          pr2: '',
          triangleA2: '',
          akb2: '',
          pin61MK2: '',
          c35Akb2: '',
          c35Ip2: '',
          vd252: '',
          vbAT2: '',
          pin60MKAkb2: '',
          pin60MKIp2: '',
          vd292: '',
          inotMA2: '',
          r662: '',
          lNoObstacle2: '',
          lWithObstacle2: '',
          pin1DA42: '',
          pin8DA42: '',
        },
        {
          date: '',
          controlSum: '',
          k3: '',
          pit: '',
          c35: '',
          pin7MK: '',
          Upit: '',
          c41: '',
          c14: '',
          c1: '',
          c45: '',
          triangle: '',
          downTriangle: '',
          spO2: '',
          pr: '',
          triangleA: '',
          akb: '',
          pin61MK: '',
          c35Akb: '',
          c35Ip: '',
          vd25: '',
          vbAT: '',
          pin60MKAkb: '',
          pin60MKIp: '',
          vd29: '',
          inotMA: '',
          r66: '',
          lNoObstacle: '',
          lWithObstacle: '',
          pin1DA4: '',
          pin8DA4: '',
          triangle2: '',
          downTriangle2: '',
          spO22: '',
          pr2: '',
          triangleA2: '',
          akb2: '',
          pin61MK2: '',
          c35Akb2: '',
          c35Ip2: '',
          vd252: '',
          vbAT2: '',
          pin60MKAkb2: '',
          pin60MKIp2: '',
          vd292: '',
          inotMA2: '',
          r662: '',
          lNoObstacle2: '',
          lWithObstacle2: '',
          pin1DA42: '',
          pin8DA42: '',
        },
        {
          date: '',
          controlSum: '',
          k3: '',
          pit: '',
          c35: '',
          pin7MK: '',
          Upit: '',
          c41: '',
          c14: '',
          c1: '',
          c45: '',
          triangle: '',
          downTriangle: '',
          spO2: '',
          pr: '',
          triangleA: '',
          akb: '',
          pin61MK: '',
          c35Akb: '',
          c35Ip: '',
          vd25: '',
          vbAT: '',
          pin60MKAkb: '',
          pin60MKIp: '',
          vd29: '',
          inotMA: '',
          r66: '',
          lNoObstacle: '',
          lWithObstacle: '',
          pin1DA4: '',
          pin8DA4: '',
          triangle2: '',
          downTriangle2: '',
          spO22: '',
          pr2: '',
          triangleA2: '',
          akb2: '',
          pin61MK2: '',
          c35Akb2: '',
          c35Ip2: '',
          vd252: '',
          vbAT2: '',
          pin60MKAkb2: '',
          pin60MKIp2: '',
          vd292: '',
          inotMA2: '',
          r662: '',
          lNoObstacle2: '',
          lWithObstacle2: '',
          pin1DA42: '',
          pin8DA42: '',
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
      const inputs = Array.from(document.querySelectorAll('textarea'));
      const currentIndex = inputs.indexOf(currentInput);
      const nextInput = inputs[currentIndex + 1];
      if (nextInput) {
        nextInput.focus();
      }
    },
    autoResize(event) {
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
  margin-bottom: 100px
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
  min-width: 70px;
}
select {
  width: 60px;
  box-sizing: border-box;
}
</style>