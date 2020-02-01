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
                <v-toolbar-title>Bit Calculator</v-toolbar-title>
                <v-spacer />

              </v-toolbar>
              <v-card-text>
                <v-form>
                    <v-text-field
                        label="X"
                        placeholder="0x00"
                        outlined
                    ></v-text-field>
                    <v-text-field
                        label="Y"
                        placeholder="0x00"
                        outlined
                    ></v-text-field>
                    <v-text-field
                        label="Result"
                        placeholder="0x00"
                        outlined
                        disabled
                    ></v-text-field>

                    <v-btn small>&lt;&lt;</v-btn>
                    <v-btn small>&gt;&gt;</v-btn>
                    <v-btn small>&amp;</v-btn>
                    <v-btn small>^</v-btn>
                    <v-btn small>~</v-btn>
                    <v-btn small>|</v-btn>
                </v-form>
              </v-card-text>
              <v-card-actions>
                <v-spacer />
                <v-btn color="primary">Calculate</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
  export default {
    props: {
      source: String,
    },
  }
</script>