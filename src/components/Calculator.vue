<template>
  <v-app id="inspire">
    <v-content>
      <v-container
        class="fill-height"
        fluid
      >
        <v-row
          align="center"
          justify="center"
        >
          <v-col
            cols="12"
            sm="8"
            md="4"
          >
            <v-card class="elevation-12">
              <v-toolbar
                color="primary"
                dark
                flat
              >
                <v-toolbar-title>Bitwise Calculator</v-toolbar-title>
                <v-spacer />

              </v-toolbar>

              <v-card-text>
                <v-form
                    @submit.prevent="calculate"
                    id="calc-form"
                >

                    <MultiInput
                        label="x"
                        placeholder="0x00"
                        :val.sync="calc.formX"
                    />

                    <MultiInput
                        label="Y"
                        placeholder="0x00"
                        :val.sync="calc.formY" 
                    />

                    <Functions/>

                    <MultiInput
                        label="Result"
                        placeholder="0x00"
                        :val.sync="calc.formR"
                        :disabled=true
                    />

                </v-form>
              </v-card-text>
              <v-card-actions>
                <v-spacer />
                <v-btn color="primary" type="submit" form="calc-form">Calculate</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import MultiInput from './MultiInput';
import Functions from './Functions';

export default {
    components: {
        MultiInput,
        Functions
    },
    props: {},
    data() {
        return {
            calc : {
                formX: '',
                formY: '',
                formR: ''
            }
        }
    },
    methods: {

        calculate(e) {
            console.log(e,'calc');
        }
    }
}
</script>