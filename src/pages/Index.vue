<template>
  <q-page class="container">
    <div
      class="row q-col-gutter-y-xl q-gutter-y-lg q-col-gutter-x-lg q-pa-lg items-stretch"
    >
      <div class="col-md-4 col-12">
        <material-chart-card type="bar" :data="seriesColumn" :options="columnOptions" color="primary">
          <h5 class="card-title text-weight-light q-mt-sm q-ml-sm q-my-none">
            Website Views
          </h5>

          <p class="d-inline-flex text-weight-light q-ml-sm q-mt-xs">
            Last Campaign Performance
          </p>

          <template v-slot:actions>
            <q-icon class="q-mr-xs" size="10px" name="mdi-clock-outline" />
            <span class="caption text-grey text-weight-light"
            >updated 10 minutes ago</span
            >
          </template>
        </material-chart-card>
      </div>
      <div class="col-md-4 col-12">
        <material-chart-card type="line" :data="series" :options="chartOptions" color="secondary">
          <h5 class="card-title text-weight-light q-mt-sm q-ml-sm q-my-none">
            Website Views
          </h5>

          <p class="d-inline-flex text-weight-light q-ml-sm q-mt-xs">
            Last Campaign Performance
          </p>

          <template v-slot:actions>
            <q-icon class="q-mr-xs" size="10px" name="mdi-clock-outline" />
            <span class="caption text-grey text-weight-light"
              >updated 10 minutes ago</span
            >
          </template>
        </material-chart-card>
      </div>
      <div class="col-md-4 col-12">
        <material-chart-card type="bar" :data="seriesColumn" :options="columnOptions" color="primary">
          <h5 class="card-title text-weight-light q-mt-sm q-ml-sm q-my-none">
            Website Views
          </h5>

          <p class="d-inline-flex text-weight-light q-ml-sm q-mt-xs">
            Last Campaign Performance
          </p>

          <template v-slot:actions>
            <q-icon class="q-mr-xs" size="10px" name="mdi-clock-outline" />
            <span class="caption text-grey text-weight-light"
            >updated 10 minutes ago</span
            >
          </template>
        </material-chart-card>
      </div>

      <div class="col-md-3 col-12" v-for="i in 4" :key="i">
        <material-stats-card
          color="info"
          icon="mdi-twitter"
          title="Followers"
          value="+245"
          sub-icon="mdi-clock"
          sub-text="Just Updated"
        />
      </div>

      <div class="col-12 col-md-6">
        <material-card color="accent" class="q-px-md q-py-dm">
          <template v-slot:heading>
            <div class="text-h6 text-weight-light text-white">
              Employees Stats
            </div>

            <div class="text-subtitle2 text-weight-light text-white">
              New employees on 15th September, 2016
            </div>
          </template>
          Tabell
        </material-card>
      </div>
    </div>
  </q-page>
</template>

<script>
import MaterialStatsCard from "../components/MaterialStatsCard";
import MaterialCard from "../components/MaterialCard";
import MaterialChartCard from "../components/MaterialChartCard";
export default {
  name: "PageIndex",
  components: {
    MaterialChartCard,
    MaterialCard,
    MaterialStatsCard,
  },
  data() {
    return {
      colors: [
        "linear-gradient( 135deg, #ABDCFF 10%, #0396FF 100%)",
        "linear-gradient( 135deg, #2AFADF 10%, #4C83FF 100%)",
        "linear-gradient( 135deg, #FFD3A5 10%, #FD6585 100%)",
        "linear-gradient( 135deg, #EE9AE5 10%, #5961F9 100%)"
      ],
      series: [
        {
          name: "Desktops",
          data: [10, 41, 35, 51, 49, 62, 69, 91, 99]
        }
      ],
      chartOptions: {
        colors: ["#033e85", "#17ead9", "#f02fc2"],
        chart: {
          zoom: {
            enabled: false
          },
          toolbar: {
            show: false
          }
        },
        grid: {
          show: true,
          strokeDashArray: 0,
          xaxis: {
            lines: {
              show: false
            }
          }
        },
        stroke: {
          curve: "straight"
        },
        dropShadow: {
          enabled: true,
          opacity: 0.3,
          blur: 5,
          left: -7,
          top: 22
        },
        dataLabels: {
          enabled: false
        },
        xaxis: {
          categories: [
            "Jan",
            "Feb",
            "Mar",
            "Apr",
            "May",
            "Jun",
            "Jul",
            "Aug",
            "Sep"
          ],
          labels: {
            style: {
              colors: "#fff"
            }
          }
        },
        yaxis: {
          labels: {
            style: {
              color: "#fff",
              cssClass: 'chart__label',
            }
          }
        }
      },
      seriesColumn: [{
        name: 'Net Profit',
        data: [44, 55, 57, 56, 61, 58, 63, 60, 66]
      }],
      columnOptions: {
        colors: ['#00afac', '#17ead9', '#f02fc2'],
        grid: {
          show: true,
          strokeDashArray: 0,
          xaxis: {
            lines: {
              show: true
            }
          }
        },
        chart: {
          zoom: {
            enabled: false
          },
          toolbar: {
            show: false
          }
        },
        fill: {
          type: 'gradient',
          gradient: {
            shade: 'dark',
            type: 'vertical',
            shadeIntensity: 0.5,
            inverseColors: false,
            opacityFrom: 1,
            opacityTo: 0.8,
            stops: [0, 100]
          }
        },
        dataLabels: {
          enabled: false
        },
        stroke: {
          width: 0
        },
        xaxis: {
          categories: ['Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct'],
          labels: {
            style: {
              colors: '#fff'
            }
          }
        },
        yaxis: {
          labels: {
            show: true,
            style: {
              color: '#fff',
              cssClass: 'chart__label',
            }
          }
        },
        tooltip: {
          y: {
            formatter: function (val) {
              return '$ ' + val + ' thousands'
            }
          }
        }
      }
    };
  }
};
</script>

<style lang="sass">
.chart__label
  fill: #fff
</style>
