<template>
  <div>
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
            <td :rowspan="2">{{ row.date }}</td>
            <td :rowspan="2">{{ row.controlSum }}</td>
            <td :rowspan="2">{{ row.k3 }}</td>
            <td :rowspan="2">{{ row.pit }}</td>
            <td :rowspan="2">{{ row.c35 }}</td>
            <td :rowspan="2">{{ row.pin7MK }}</td>
            <td>{{ row.Upit }}</td>
            <td>{{ row.c41 }}</td>
            <td>{{ row.c14 }}</td>
            <td>{{ row.c1 }}</td>
            <td>{{ row.c45 }}</td>
            <td>{{ row.triangle }}</td>
            <td>{{ row.downTriangle }}</td>
            <td>{{ row.spO2 }}</td>
            <td>{{ row.pr }}</td>
            <td>{{ row.triangleA }}</td>
            <td>{{ row.akb }}</td>
            <td>{{ row.pin61MK }}</td>
            <td>{{ row.c35Akb }}</td>
            <td>{{ row.c35Ip }}</td>
            <td>{{ row.vd25 }}</td>
            <td>{{ row.vbAT }}</td>
            <td>{{ row.pin60MKAkb }}</td>
            <td>{{ row.pin60MKIp }}</td>
            <td>{{ row.vd29 }}</td>
            <td>{{ row.inotMA }}</td>
            <td>{{ row.r66 }}</td>
            <td>{{ row.lNoObstacle }}</td>
            <td>{{ row.lWithObstacle }}</td>
            <td>{{ row.pin1DA4 }}</td>
            <td>{{ row.pin8DA4 }}</td>
          </tr>
          <tr>
            <td>{{ row.Upit2 }}</td>
            <td>{{ row.c412 }}</td>
            <td>{{ row.c142 }}</td>
            <td>{{ row.c12 }}</td>
            <td>{{ row.c452 }}</td>
            <td>{{ row.triangle2 }}</td>
            <td>{{ row.downTriangle2 }}</td>
            <td>{{ row.spO22 }}</td>
            <td>{{ row.pr2 }}</td>
            <td>{{ row.triangleA2 }}</td>
            <td>{{ row.akb2 }}</td>
            <td>{{ row.pin61MK }}</td>
            <td>{{ row.c35Akb2 }}</td>
            <td>{{ row.c35Ip2 }}</td>
            <td>{{ row.vd252 }}</td>
            <td>{{ row.vbAT2 }}</td>
            <td>{{ row.pin60MKAkb2 }}</td>
            <td>{{ row.pin60MKIp2 }}</td>
            <td>{{ row.vd292 }}</td>
            <td>{{ row.inotMA2 }}</td>
            <td>{{ row.r662 }}</td>
            <td>{{ row.lNoObstacle2 }}</td>
            <td>{{ row.lWithObstacle2 }}</td>
            <td>{{ row.pin1DA42 }}</td>
            <td>{{ row.pin8DA42 }}</td>
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
};
</script>

<style>
  table {
    width: 100%;
    border-collapse: collapse;
  }
  th, td {
    border: 1px solid #000;
    padding: 5px;
    text-align: center;
  }
</style>
