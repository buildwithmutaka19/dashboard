<script>
import MetricTarget from '@/edit/autoscaling.horizontalpodautoscaler/metric-target';
import MetricIdentifier from '@/edit/autoscaling.horizontalpodautoscaler/metric-identifier';

export const DEFAULT_POD_METRIC = {
  type:   'io.k8s.api.autoscaling.v2beta2.podsmetricsource',
  metric: {
    name:     '',
    selector: {
      matchExpressions: [],
      matchLabels:      {},
    },
  },
  target: {
    type:               'AverageValue',
    averageValue:       50,
  },
};

export default {
  components: {
    MetricTarget,
    MetricIdentifier,
  },
  props: {
    value: {
      type:    Object,
      default: () => ({
        name:   '',
        target: {},
      }),
    },

    mode: {
      type:    String,
      default: 'create',
    },
  },
};
</script>

<template>
  <div>
    <div class="row mb-20">
      <MetricTarget v-model="value.target" :mode="mode" type="pod" />
    </div>
    <div class="row">
      <MetricIdentifier v-model="value.metric" :mode="mode" />
    </div>
  </div>
</template>
