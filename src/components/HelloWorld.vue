<template>
  <div class="hello">

    <h1> G A B I N E T E S </h1>
    <div class="container">
      <div class="row" v-for="(se, index) in subestaciones" :key="index">

        <div v-for="(device, index) in se.subestacion" :key="index" class="col">
          <div class="card own">
            <qrcode-vue :value="('http://10.28.80.118:8080/rack/' + device.idGabinete)" :size="size" level="H"
              :margin="1" />
            <div class="card-body" style="background-color:black; padding: 0rem !important;">
              <h5 class="card-title text-on-card">{{ device.nombre }}</h5>
            </div>
          </div>
          <br>
        </div>
      </div>
    </div>


    <h1> E Q U I P O S </h1>
    <div class="container">
      <div class="row" v-for="(se, index) in subestaciones" :key="index">

        <template v-for="(device, index) in se.subestacion" :key="index">

          <div v-for="(dev, index2) in device.equipos" :key="index2">

            <div class="col">

              <div class="card own">

                <qrcode-vue :value="('http://10.28.80.118:8080/rack/' + dev.R3)" :size="size" level="H" :margin="1" />
                <div class="card-body" style="background-color:black; padding: 0rem !important;">
                  <h5 class="card-title text-on-card">{{ dev.R3 }}</h5>
                </div>
              </div>
            </div>
            <br>

          </div>


          <br>
        </template>
      </div>
    </div>








  </div>
</template>
 
<script>

import QrcodeVue from 'qrcode.vue'

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      value: 'https://example.com',
      size: 250,
      devices: [
        { url: 'google.com', name: 'google' },
        { url: 'yahoo.com', name: 'yahoo' },
        { url: 'brave.com', name: 'brave' },
      ],
      subestaciones: [
        {
          nombre: 'NIZ',
          subestacion: [
            {
              nombre: 'A1',
              idGabinete: 1,
              equipos: [
                { R3: "2042442", id: 9, UGabinete: "A1", PGabinete: 1, TipoId: 4, Marca: "LT NIZ-93070-VAD", Tipo: "T-RADOPL", NombreEquipo: "POWER LINK", Img: "powerlink.png" },
                { R3: "2125565", id: 10, UGabinete: "A1", PGabinete: 2, TipoId: 5, Marca: "LT NIZ-93070-VAD", Tipo: "T-TELEPRO", NombreEquipo: "SWT3000", Img: "swt3000.png" },
              ]
            },
            {
              nombre: 'A2',
              idGabinete: 2,
              equipos: [
                { R3: "100", id: 1, UGabinete: "A02", PGabinete: "01", TipoId: 7, Marca: "ODF", Tipo: "T-DISTOPT", NombreEquipo: "GTAC", Img: 'gtag.png' }
              ]
            },
            {
              nombre: 'A3',
              idGabinete: 3,
              equipos: [
                { R3: "19422550", id: 1, UGabinete: "A3", PGabinete: "38", TipoId: 2, Marca: "CISCO", Tipo: "T-SWITCH", NombreEquipo: "CGS-2520", Img: "cisco-2520.png" },
                { R3: "1416767", id: 2, UGabinete: "A3", PGabinete: "21", TipoId: 2, Marca: "CISCO", Tipo: "T-SWITCH", NombreEquipo: "3560", Img: "cisco-3560.png" }
              ]
            },
            {
              nombre: 'A4',
              idGabinete: 4,
              equipos: [
                { R3: "2195455", id: 1, UGabinete: "A4", PGabinete: 37, TipoId: 1, Marca: "CISCO", Tipo: "T-ROUTER", NombreEquipo: "ASR-903", Img: "cisco-asr903.png" },
                { R3: "766900", id: 2, UGabinete: "A4", PGabinete: 33, TipoId: 1, Marca: "CISCO", Tipo: "T-ROUTER", NombreEquipo: "3945", Img: "cisco-3945.png" },
                { R3: "1416759", id: 3, UGabinete: "A4", PGabinete: 29, TipoId: 2, Marca: "CISCO", Tipo: "T-SWITCH", NombreEquipo: "3560", Img: "cisco-3560.png" },
                // { R3: "0", id: 4, UGabinete: "A4", PGabinete: 24, TipoId: 3, Marca: "CISCO", Tipo: "T-PP", NombreEquipo: "PatchPanel", Img: "patchpanel2.png" }
              ]
            },
            {
              nombre: 'A5',
              idGabinete: 5,
              equipos: [
                { R3: "1942255", id: 5, UGabinete: "A5", PGabinete: "40", TipoId: 2, Marca: "CISCO", Tipo: "T-SWITCH", NombreEquipo: "2520", Img: "cisco-2520.png" },
                { R3: "2449754", id: 6, UGabinete: "A5", PGabinete: "33", TipoId: 2, Marca: "ARUBA", Tipo: "T-ROUTER", NombreEquipo: "2930F", Img: "aruba-2930f1.png" },
                { R3: "749941", id: 7, UGabinete: "A5", PGabinete: "26", TipoId: 2, Marca: "CISCO", Tipo: "T-SWITCH", NombreEquipo: "3560", Img: "cisco-3560.png" },
                { R3: "7499", id: 8, UGabinete: "A5", PGabinete: "19", TipoId: 2, Marca: "TPLINK", Tipo: "T-SWITCH", NombreEquipo: "TPLINK", Img: 'tplinkSwitch.png' }
              ]
            },
            {
              nombre: 'A7',
              idGabinete: 7,
              equipos: [
                { R3: "1195704", id: 11, UGabinete: "A7", PGabinete: 1, TipoId: 5, Marca: "LT NIZ-73480-CEX", Tipo: "T-RADOPL", NombreEquipo: "esb2000i", Img: "esb2000i.png" }
              ]
            },
            {
              nombre: 'A29',
              idGabinete: 29,
              equipos: [
                { R3: "2050859", id: 12, UGabinete: "A29", PGabinete: 1, TipoId: 5, Marca: "LT NIZ-93040-RMY", Tipo: "T-RADOPL", NombreEquipo: "POWER LINK", Img: "powerlink.png" },
                { R3: "2050860", id: 13, UGabinete: "A29", PGabinete: 2, TipoId: 6, Marca: "LT NIZ-93040-RMY", Tipo: "T-TELEPRO", NombreEquipo: "SWT3000", Img: "swt3000.png" }
              ]
            },
            {
              nombre: 'A30',
              idGabinete: 30,
              equipos: [
                { R3: "749259", id: 14, UGabinete: "A30", PGabinete: 1, TipoId: 5, Marca: "LT NIZ-93060-BLM", Tipo: "T-RADOPL", NombreEquipo: "esb2000i", Img: "esb2000i.png" }
              ]
            },
            {
              nombre: 'A31',
              idGabinete: 31,
              equipos: [
                { R3: "1515348", id: 1, UGabinete: "A31", PGabinete: "1", TipoId: 7, Marca: "FC", Tipo: "T-DISTOPT", NombreEquipo: "CANCUN", Img: "odf-fc.png" }
              ]
            },
            {
              nombre: 'A33',
              idGabinete: 33,
              equipos: [
                { R3: "21619", "id": 1, UGabinete: "A33", PGabinete: "01", TipoId: 9, Marca: "NIZ-PMO-ZH", Tipo: "T-TOPTICA", NombreEquipo: "FOX 515", Img: 'Fox.png' }
              ]
            },
            {
              nombre: 'B2',
              idGabinete: 35,
              equipos: [
                { R3: "2195453", id: 1, UGabinete: "B2", PGabinete: "1", TipoId: 7, Marca: "FC", Tipo: "T-DISTOPT", NombreEquipo: "BONFIL", Img: "odf-fc.png" },
                { R3: "1515070", id: 2, UGabinete: "B2", PGabinete: "2", TipoId: 7, Marca: "FC", Tipo: "T-DISTOPT", NombreEquipo: "PUERTO MORELOS", Img: "odf-fc.png" },
                { R3: "2195457", id: 3, UGabinete: "B2", PGabinete: "3", TipoId: 7, Marca: "FC", Tipo: "T-DISTOPT", NombreEquipo: "NICTE HA", Img: "odf-fc.png" }
              ]
            },
            {
              nombre: 'B3',
              idGabinete: 36,
              equipos: [
                { R3: "1515068", id: 1, UGabinete: "B3", PGabinete: "1", TipoId: 7, Marca: "SC", Tipo: "T-DISTOPT", NombreEquipo: "NIZ M.O MM", Img: "odf-sc.png" },
                { R3: "1515620", id: 2, UGabinete: "B3", PGabinete: "2", TipoId: 7, Marca: "SC", Tipo: "T-DISTOPT", NombreEquipo: "CTG NIZ", Img: "odf-sc.png" },
                { R3: "1515242", id: 3, UGabinete: "B3", PGabinete: "3", TipoId: 7, Marca: "SC", Tipo: "T-DISTOPT", NombreEquipo: "NIZ M.O SM", Img: "odf-sc.png" },
                { R3: "1515349", id: 4, UGabinete: "B3", PGabinete: "4", TipoId: 7, Marca: "SC", Tipo: "T-DISTOPT", NombreEquipo: "ALMACEN", Img: "odf-sc.png" }
              ]
            },
            {
              nombre: 'B4',
              idGabinete: 37,
              equipos: [
                { R3: "1515067", id: 1, UGabinete: "B4", PGabinete: "1", TipoId: 7, Marca: "SC", Tipo: "T-DISTOPT", NombreEquipo: "BALAM", Img: "odf-sc.png" },
                { R3: "2017965", id: 2, UGabinete: "B4", PGabinete: "2", TipoId: 7, Marca: "SC", Tipo: "T-DISTOPT", NombreEquipo: "CONF NIZ 1", Img: "odf-sc.png" },
                { R3: "2195452", id: 3, UGabinete: "B4", PGabinete: "3", TipoId: 7, Marca: "SC", Tipo: "T-DISTOPT", NombreEquipo: "CONF NIZ 2", Img: "odf-sc.png" }
              ]
            },
            {
              nombre: 'B6',
              idGabinete: 39,
              equipos: [
                { R3: "1167806", id: 1, UGabinete: "B06", PGabinete: "01", TipoId: 9, Marca: "NIZ-CNC-BNI", Tipo: "T-TOPTICA", NombreEquipo: "FOX 515", Img: 'Fox.png' }
              ]
            },
            {
              nombre: 'B7',
              idGabinete: 40,
              equipos: [
                { R3: "1167815", id: 15, UGabinete: "b7", PGabinete: 1, TipoId: 6, Marca: "LT NIZ-93170-RMY", Tipo: "T-TELEPRO", NombreEquipo: "NSD570", Img: "nsd570.png" },
                { R3: "1167872", id: 16, UGabinete: "b7", PGabinete: 2, TipoId: 6, Marca: "LT NIZ-93040-RMY", Tipo: "T-TELEPRO", NombreEquipo: "NSD570", Img: "nsd570.png" },
                { R3: "1942272", id: 17, UGabinete: "b7", PGabinete: 3, TipoId: 6, Marca: "LT NIZ-93070-VAD", Tipo: "T-TELEPRO", NombreEquipo: "NSD570", Img: "nsd570.png" },
                { R3: "1546740", id: 17, UGabinete: "b7", PGabinete: 4, TipoId: 6, Marca: "LT NIZ-93060-BLM", Tipo: "T-TELEPRO", NombreEquipo: "NSD570", Img: "nsd570.png" }
              ]
            },
            {
              nombre: 'B8',
              idGabinete: 41,
              equipos: [
                { R3: "1515351", id: 1, UGabinete: "B8", PGabinete: "1", TipoId: 7, Marca: "FC", Tipo: "T-DISTOPT", NombreEquipo: "PCN-VAD", Img: "odf-fc.png" }
              ]
            },
            {
              nombre: 'B9',
              idGabinete: 42,
              equipos: [
                { R3: "778296", id: 1, UGabinete: "B09", PGabinete: "01", TipoId: 9, Marca: "NIZ-RMY", Tipo: "T-TOPTICA", NombreEquipo: "FOX 515", Img: 'Fox.png' },

                { R3: "201595", id: 1, UGabinete: "B09", PGabinete: "02", TipoId: 9, Marca: "NIZ-MPA-PCN", Tipo: "T-TOPTICA", NombreEquipo: "FOX 615", Img: 'Fox615.png' }

              ]
            },
            {
              nombre: 'B10',
              idGabinete: 43,
              "equipos": [
                { R3: "2010800", id: 1, UGabinete: "B10", PGabinete: "01", TipoId: 8, Marca: "ECI TELECOM", Tipo: "T-TOPTICA", NombreEquipo: "NTP-1020", Img: "cisco-1020.png" }
              ]
            },
            {
              nombre: 'B11',
              idGabinete: 44,
              equipos: [
                { R3: "2049156", id: 18, UGabinete: "B11", PGabinete: 1, TipoId: 5, Marca: "LT NIZ-93170-RMY", Tipo: "T-RADOPL", NombreEquipo: "POWER LINK", Img: "powerlink.png" },
                { R3: "2049157", id: 19, UGabinete: "B11", PGabinete: 2, TipoId: 6, Marca: "LT NIZ-93170-RMY", Tipo: "T-TELEPRO", NombreEquipo: "SWT3000", Img: "swt3000.png" }
              ]
            },
            {
              nombre: 'B16',
              idGabinete: 53,
              equipos: [
                { R3: "2293907", "id": 1, "UGabinete": "B20", "PGabinete": "01", "TipoId": 10, "Marca": "CISCO", "Tipo": "T-EXTTEL", "NombreEquipo": "EXT 35102", Img: 'telefono.png' }
              ]
            },
          ]
        },
        {
          nombre: 'BLM',
          subestacion: []
        }

      ]
    }
  },
  components: {
    QrcodeVue,
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.own {
  border: solid black 5px;
  border-radius: 10px;
  width: 260px;

}

.text-on-card {
  color: white;
  font-size: 45px;
  font-weight: bold;
}

.card-title {
  margin-bottom: 0 !important;
  margin-top: .5rem !important;
}
</style>
