<template>
  <div class="list">
    <div class="index-title">赞助表</div>
    <div class="index-title" v-if="index === 2">除了自定义称号，其他的都是唯一的</div>
    <div class="list-main" v-if="index === k" v-for="(i, k) in arr" :key="k">
      <div class="table">
        <v-data-table
          :headers="headers"
          :items="i.arr"
          :rows-per-page-items="[{ text: '$vuetify.dataIterator.rowsPerPageAll', 'value': -1 }]"
          class="elevation-1"
        >
          <template slot="items" slot-scope="props">
            <td>
              <img :src="props.item.img" v-if="props.item.img" alt>
              <span v-if="!props.item.img" :class="'sprite-icon sprite-icon-'+props.item.id"></span>
            </td>
            <td>{{ props.item.name }}</td>
            <td class="td-price">{{ getPrice(props.item) }}</td>
            <td>
              <v-btn @click="dialog=true" color="primary" v-if="!props.item.kong">购买</v-btn>
            </td>
          </template>
        </v-data-table>
      </div>
    </div>
    <v-dialog v-model="dialog" width="1180">
      <v-card>
        <v-card-title class="headline grey lighten-2" primary-title>请选择支付方式（注意备注自己的游戏ID）</v-card-title>

        <v-card-text>
          <v-tabs v-model="active" dark slider-color="yellow">
            <v-tab v-for="n in play" :key="n" ripple>{{ n }}</v-tab>
          </v-tabs>
          <div class="index-title">{{play[active]}} 支付（注意备注自己的游戏ID）</div>
          <img v-if="active===0" class="palyImg" src="/static/qq.JPG" alt>
          <img v-if="active===1" class="palyImg" src="/static/wx.JPG" alt>
          <img v-if="active===2" class="palyImg" src="/static/zfb.JPG" alt>
        </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="primary" flat @click="dialog = false">关闭窗口</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
import list1 from "./list_poke.js";
import list2 from "./list_power.js";
import list3 from "./list_title.js";
import list4 from "./list_other.js";
export default {
  data() {
    return {
      index: 0,
      dialog: false,
      active: 0,
      play: ["QQ", "微信", "支付宝"],
      headers: [
        {
          text: "#",
          align: "center",
          sortable: false,
          value: "img"
        },
        {
          text: "名称",
          align: "center",
          sortable: false,
          value: "name"
        },
        {
          text: "价格",
          align: "center",
          sortable: false,
          value: "pic"
        },
        {
          text: "操作",
          align: "center",
          sortable: false,
          value: "opt"
        }
      ],
      arr: [list1, list2, list3, list4]
    };
  },
  methods: {
    toPage(n) {
      this.index = n;
    },
    getPrice(i) {
      if (i.kong) {
        return i.kong;
      }
      if (i.price) {
        return i.price;
      } else {
        if (i.zz > 600) {
          return i.zz / 10;
        } else {
          return i.zz / 20;
        }
      }
    }
  }
};
</script>
<style>
.list {
  text-align: center;
  padding-top: 48px;
}
.table {
  width: 80%;
  margin: 0 auto;
}
.td-price {
  font-size: 16px !important;
  font-weight: bold !important;
  color: #f5281b;
}
.palyImg {
  width: 400px;
}
</style>
