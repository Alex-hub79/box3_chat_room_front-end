<template>
  <v-container>
    <v-row justify="center">
      <!-- 让用户登记昵称弹出的对话框部分 -->
      <v-dialog v-model="dialog" persistent max-width="600px">
        <v-card>
          <v-card-title>
            <span class="text-h5">信息登记</span>
          </v-card-title>
          <v-card-text class="px-5">
            <v-col cols="12">
              <v-text-field label="昵称*" required></v-text-field>
            </v-col>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" text @click="dialog = false"
              >确定</v-btn
            >
          </v-card-actions>
        </v-card>
      </v-dialog>

      <!-- 主要聊天界面 -->
      <v-app id="inspire">
        <v-navigation-drawer
          v-model="drawer"
          app
          class="pt-4"
          mini-variant
          right
          mini-variant-width="300px"
        >
          <v-list disabled>
            <v-subheader>在线用户</v-subheader>
            <v-list-item-group v-model="selectedItem" color="primary">
              <v-list-item
                v-model="selectedItem"
                color="primary"
                v-for="n in online_user_list"
                :key="n"
                link
              >
                <v-list-item-content>
                  <v-list-item-title>
                    <v-icon>{{ icons.mdiAccount }}</v-icon>
                    {{ n }}
                  </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </v-list-item-group>
          </v-list>
        </v-navigation-drawer>

        <v-main>
          <!--  -->
        </v-main>
      </v-app>
      <div class="input">
        <v-textarea
          class="input_msg"
          v-model="msg"
          name="input-7-1"
          filled
          label="输入消息"
          no-resize
          clearable="true"
        ></v-textarea>
        <v-btn @click="send_msg" class="send" outlined color="indigo">
          <v-icon>mdi-send</v-icon>
          发送消息
        </v-btn>
        
        <v-dialog v-model="set" scrollable max-width="500px">
          <template v-slot:activator="{ on, attrs }">
            <v-btn
              outlined
              color="indigo"
              dark
              class="setting"
              v-bind="attrs"
              v-on="on"
            >
              <v-icon>mdi-cog-outline</v-icon>
              设置
            </v-btn>
          </template>
          <v-card>
            <v-card-title><v-icon>mdi-cog-outline</v-icon>设置选项</v-card-title>
            <v-divider> </v-divider>
            <v-card-text style="height: 300px">
              <v-col cols="6">
                <v-container
    class="px-0"
    fluid
  >
    <v-switch
      v-model="switch1"
      label="夜间模式"
      append-icon="mdi-brightness-6"
      @change="dark_theme"
    >
    </v-switch>
  </v-container>
              </v-col>
            </v-card-text>
            <v-divider> </v-divider>
            <v-card-actions>
              <v-btn color="blue darken-1" text @click="set = false">
                保存并关闭
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </div>

      <div class="chat_msg">
        <v-list two-line class="main_chat">
          <template v-for="n in online_user_list">
            <v-list-item :key="n">
              <v-list-item-content>
                <v-list-item-title>{{ n }}</v-list-item-title>

                <v-list-item-subtitle> 嘿！大家好！ </v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
          </template>
        </v-list>
      </div>
    </v-row>
  </v-container>
</template>

<script>
import { mdiAccount } from "@mdi/js";
export default {
  name: "chat",
  data: () => ({
    icons: {
      mdiAccount,
    },
    dialog: true,
    set: false,
    switch1: false,
    online_user_list: [
      "吉吉喵的小号",
      "吉吉喵!",
      "吉吉喵的徒弟",
      "吉喵喵",
      "喵喵吉祥",
      "吉吉喵",
      "吉吉喵BOⅩ2",
      "山里的吉吉喵吉吉喵家族",
      "A--喵吉家族明星",
      "吉吉喵AbHg",
      "吉吉喵的小伙伴",
      "开朗的吉吉喵(琉璃小喵)",
      "吉吉喵的ltltltlt",
      "我是吉吉喵",
      "V字喵吉",
      "没名某人的徒弟",
      "没各某人",
      "没名字的某人的小号之金币救济号",
      "没名字的某人的小号3号",
      "没名字的某人的小号2号",
      "没名某人是傻逼。",
      "没有名字的某人",
    ],
  }),
  methods: {
    send_msg: async function () {
      console.log("hhh");
      console.log(this.msg);
    },

    dark_theme: async function () {
      if (this.switch1 === true) {
        this.$vuetify.theme.dark = true;
        console.log("hhhjhh");
      }
      else{
        this.$vuetify.theme.dark = false;
      }
    },
  },
};
</script>

<style src='./chat.css'></style>