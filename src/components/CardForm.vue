<template>
  <v-form style="margin-top: 100px"
    ref="form"
    v-model="valid"
    lazy-validation
  >
    <v-layout row>
      <v-flex xs2 offset-xs3>

        <v-text-field
          v-model="name"
          :counter="11"
          :rules="nameRules"
          label="Nombre"
          required
        ></v-text-field>
      </v-flex>

      <v-flex xs2>
        <v-select
          v-model="average"
          :items="numbers"
          :rules= "numberRules"
          label="Media"
          required
        ></v-select>
      </v-flex>

      <v-flex xs2>
        <v-select
          v-model="speed"
          :items="numbers"
          :rules="[v => !!v || 'Item is required']"
          label="Velocidad"
          required
        ></v-select>
      </v-flex>
    </v-layout>


    <v-layout row>
      <v-flex xs2 offset-xs3>
        <v-select
          v-model="shot"
          :items="numbers"
          :rules="[v => !!v || 'Item is required']"
          label="Tiro"
          required
        ></v-select>
      </v-flex>

      <v-flex xs2>
        <v-select
          v-model="pass"
          :items="numbers"
          :rules="[v => !!v || 'Item is required']"
          label="Pase"
          required
        ></v-select>
      </v-flex>

      <v-flex xs2>
        <v-select
          v-model="dribbling"
          :items="numbers"
          :rules="[v => !!v || 'Item is required']"
          label="Regate"
          required
        ></v-select>
      </v-flex>
    </v-layout>

    <v-layout row>
      <v-flex xs2 offset-xs3>
        <v-select
          v-model="defense"
          :items="numbers"
          :rules="[v => !!v || 'Item is required']"
          label="Defensa"
          required
        ></v-select>
      </v-flex>

      <v-flex xs2>
        <v-select
          v-model="physic"
          :items="numbers"
          :rules="[v => !!v || 'Item is required']"
          label="Físico"
          required
        ></v-select>
      </v-flex>

      <v-flex xs2>
        <v-select
          v-model="position"
          :items="positions"
          :rules="[v => !!v || 'Item is required']"
          label="Posición"
          required
        ></v-select>
      </v-flex>
    </v-layout>

    <v-layout row>
      <v-flex xs2 offset-xs5 >
        <v-btn
          :disabled="!valid"
          color="primary"
          @click="validate"
        >
          Crear
        </v-btn >
<!--
        <p>{{name}}, {{average}},{{speed}},{{shot}}, {{pass}}, {{dribbling}},{{defense}}, {{physic}} {{position}}</p>
-->
      </v-flex>
    </v-layout>

  </v-form>
</template>

<script>
  export default {
    data: () => ({
      valid: true,
      name: "default",
      nameRules: [
        v => !!v || 'Name is required',
        v => (v && v.length <= 11) || 'Name must be less than 10 characters'
      ],
      average: 0,
      speed: 0,
      shot: 0,
      pass: 0,
      dribbling: 0,
      defense: 0,
      physic: 0,
      position: "EI",
      positions: [
        'DC',
        'MP',
        'EI',
        'ED',
        'MI',
        'MD',
        'MCO',
        'MCD',
        'MC',
        'DFC',
        'LTI',
        'LTD',
        'PO'
      ],
      numbers: [...Array(100).keys()],
      checkbox: false
    }),
    methods: {
      validate() {
        this.$root.$emit('create', this.name, this.average, this.position, this.speed, this.shot, this.pass, this.dribbling, this.defense, this.physic);


      },
    }
  }
</script>
