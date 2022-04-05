<template>
  <v-container>
    <v-container fill-height>
    <v-row justify="center">
      <v-col cols="auto">
        <v-card raised>
          <v-card-title>Number Base Conversion Checker</v-card-title>
          <v-card-subtitle>
            Check your answer to the number base conversion question is correct or not
          </v-card-subtitle>
          <v-card-text>
            <h2 class="my-5 text-subtitle-2 font-weight-bold">Select bases</h2>

            <v-select
              v-model="originBase"
              :input="clearAnswerMessage"
              item-value="base"
              label="I'm converting from"
              :items="types"
            >
            </v-select>
            <v-select
              v-model="answerBase"
              :input="clearAnswerMessage"
              item-value="base"
              label="To"
              :items="types"
            >
            </v-select>

            <h2 class="mt-5 mb-2 text-subtitle-2 font-weight-bold">Enter your answer</h2>
            <v-text-field
              v-model="origin"
              :input="clearAnswerMessage"
              label="Origin Number"
            ></v-text-field>
            <v-text-field
              v-model="answer"
              :input="clearAnswerMessage"
              label="My Answer"
            ></v-text-field>

            <v-btn
              class="mt-5 mb-2"
              @click="check"
              color="success"
            >
              Check My Answer
            </v-btn>

            <v-alert
              outlined
              v-if="alert.message"
              :type="alert.status"
              class="mt-6 mb-0"
            >
              {{ alert.message }}
            </v-alert>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    </v-container>
  </v-container>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  name: 'ConversionChecker',
  data: () => ({
    origin: '',
    answer: '',
    alert: {
      status: '',
      message: '',
    },
    correct: 'Yes! Your answer is correct!',
    wrong: 'This is not the correct answer, please try again',
    originBase: 10,
    answerBase: 2,
    types: [
      { text: 'Decimal', base: 10 },
      { text: 'Binary', base: 2 },
      { text: 'Octal', base: 8 },
      { text: 'Hexadecimal', base: 16 },
    ],
  }),
  methods: {
    clearAnswerMessage() {
      this.alert.message = '';
    },
    check() {
      const origin = parseInt(this.origin, this.originBase);
      const answer = parseInt(this.answer, this.answerBase);
      if (origin === answer) {
        this.alert.status = 'success';
        this.alert.message = this.correct;
      } else {
        this.alert.status = 'error';
        this.alert.message = this.wrong;
      }
    },
  },
});
</script>
