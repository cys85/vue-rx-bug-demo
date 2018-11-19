<template>
  <div class="about">
    <h1>{{timestamp}}</h1>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Mixins } from 'vue-property-decorator';
import myMixin from './myMixin';
import myMixin2 from './myMixin2';
import { of } from 'rxjs';
import {tap} from 'rxjs/operators';

@Component({
  subscriptions() {

    // tslint:disable-next-line:no-console
    console.log('subscriptions');
    return {
      timestamp: of(+new Date()).pipe(tap(console.log)),
    };
  },
})
export default class About extends Mixins(myMixin, myMixin2) {}
</script>