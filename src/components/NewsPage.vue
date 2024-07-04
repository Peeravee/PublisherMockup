<template>
  <v-container>
        <v-icon
      color="#1aa29d"
      icon="mdi-cog-outline"
      size="large"
    ></v-icon><a class="ma-2" style="color: #1aa29d;">รายการข่าว</a>
    <v-row align="center" class="mt-5">
      <v-col cols="12" sm="3" >
        <div class="text-subtitle-1 text-medium-emphasis mt-n1">หมวดข่าว</div>
        <v-select
         
          :items="group"
          label="Select"
          density="compact"
          variant="outlined"
        ></v-select>
      </v-col>

      <v-col cols="12" sm="3">
        <div class="text-subtitle-1 text-medium-emphasis mt-n1">ภาค</div>
        <v-select
         
          :items="pak"
          label="Select"
          density="compact"
          variant="outlined"
        ></v-select>
      </v-col>

      <v-col cols="12" sm="3">
        <div class="text-subtitle-1 text-medium-emphasis mt-n1">จังหวัด</div>
        <v-select
          :items="distc"
          label="Select"
          density="compact"
          variant="outlined"
        ></v-select>
      </v-col>

      <v-col cols="12" sm="3">
        <div class="text-subtitle-1 text-medium-emphasis mt-n1">นักข่าว</div>
        <v-select
          :items="newser"
          label="Select"
          density="compact"
          variant="outlined"
        ></v-select>
      </v-col>
      <v-col cols="12" sm="3">
        <div class="text-subtitle-1 text-medium-emphasis mt-n1">ค้นหา หัวข้อข่าว</div>
        <v-text-field
          :items="items"
          label="คำค้นหา"
          density="compact"
          variant="outlined"
        ></v-text-field>
      </v-col>
      <v-col cols="12" sm="3">
        <div class="text-subtitle-1 text-medium-emphasis mt-n1">เลือกช่วงเวลา</div>
        <v-select
          :items="date"
          label="จากวันที่"
          density="compact"
          variant="outlined"
        ></v-select>
      </v-col>
      <v-col cols="12" sm="3" >
        <div class="text-subtitle-1 text-medium-emphasis mt-n1"> </div>
        <v-select
          :items="date"
          label="ถึงวันที่"
          density="compact"
          variant="outlined"
        ></v-select>
      </v-col>
    </v-row>
    <v-container justify="">
      <v-row align="center">
      <v-col class="text-end" cols="12">
        <v-btn  elevation="1" size="large" color="#44b5af">ค้นหา</v-btn>
        <v-btn  elevation="1" size="large" color="#525e64" class="ma-1">ดูทั้งหมด</v-btn>
      </v-col>
      </v-row>
  </v-container>
  <v-data-table
        :headers="headers"
        :items="itemstable"
        class="elevation-1"
      >
      <template v-slot:[`item.title`]="{ item }">
        <div style="color: #1aa29d;"> {{ item.title }}</div>
        </template>
        <template v-slot:[`item.type`]="{ item }">
          <v-icon style="color: red;" @click="editItem(item)">{{ item.type }}</v-icon>
        </template>
        <template v-slot:[`item.web`]="{ item }">
          <v-icon style="color: yellow;" @click="editItem(item)">{{ item.web }}</v-icon>
        </template>
        <template v-slot:[`item.tv`]="{ item }">
          <v-icon
            style="color: #1aa29d"
          >
            {{ item.tv === 1 ? 'mdi-check' : 'mdi-eye' }}
          </v-icon>
        </template>
        <template v-slot:[`item.sms`]="{ item }">
          <v-icon style="color: yellow;" @click="editItem(item)">{{ item.sms }}</v-icon>
        </template>
        <template v-slot:[`item.smsflash`]="{ item }">
          <v-icon style="color: yellow;" @click="editItem(item)">{{ item.smsflash }}</v-icon>
        </template>
        <template v-slot:[`item.pr`]="{ item }">
          <v-icon style="color: yellow;" @click="editItem(item)">{{ item.pr }}</v-icon>
        </template>
        <template v-slot:[`item.date`]="{ item }">
         <div class="mt-3" style="font-size:medium;"> {{ '25/09/2567 05.49 น.' }} </div><br>
            <v-btn class="" v-bind="props" end :style="{ color: 'grey' }" icon="mdi-note-text-outline"  depressed variant="text" border-radius="2px" @click="editItem(item)"></v-btn> 
            <v-btn class="" v-bind="props" end :style="{ color: 'grey' }" icon="mdi-tools"  depressed variant="text" border-radius="2px" @click="editItem(item)"></v-btn> 
            <v-btn class="" v-bind="props" end :style="{ color: 'grey' }" icon="mdi-delete-empty"  depressed variant="text" border-radius="2px" @click="editItem(item)"></v-btn> 

            </template>
      </v-data-table>
  </v-container>
</template>
  
  
  <script>
  export default {
    data: () => ({ 
      group:['อาชญากรรม', 'บันเทิง', 'ทั่วไทย'],
      pak:['ภาคเหนือ','ภาคตะวันออกเฉียงเหนือ','ภาคกลาง','ภาคตะวันตก','ภาคใต้'],
      distc: ['เชียงใหม่','ขอนแก่น','ชนบุรี','ตาก','กระบี่'],
      newser: ['นายสัมภาษณ์', 'ผู้ประกาศข่าว'],
      date: ['1','2','3','4','5','6','7','8','9','10','11','12','13','14','15','16','17','18','19','20','21','22','23'],
      itemsPerPage: 5,
      headers: [
        {
          title: 'หมวดข่าว',
          align: 'center',
          sortable: false,
          key: 'group',
        },
        { title: 'หัวข้อข่าว', key: 'title', align: 'center' },
        { title: 'สถานะการส่ง', key: 'status', align: 'center' },
        { title: 'บก.พิมพ์', key: 'type', align: 'center' },
        { title: 'บก.เว็บ', key: 'web', align: 'center' },
        { title: 'บก.ทีวี', key: 'tv', align: 'center' },
        { title: 'sms ปกติ', key: 'sms', align: 'center' },
        { title: 'sms ด่วน', key: 'smsflash', align: 'center' },
        { title: 'PR', key: 'pr', align: 'center' },
        { title: 'วันที่สร้าง/จัดการ', key: 'date', align: 'center' },
      ],
      itemstable: [
        { group: 'อาชญากรรม', title: 'ฆ่าอำพลางศพ ปกปิด', status: '👉 [แชร์ให้เว็บไซต์]', type:'mdi-alpha-x', web: 'mdi-circle-outline' , tv: 1, sms:'mdi-circle-outline', smsflash: 'mdi-circle-outline', pr:'mdi-circle-outline',  date: '22222'},
        { group: 'บันเทิง', title: 'ยูอินซอก เปิดปากแล้ว ! รับ ซึงรี จักหารสาวบริการ มา...', status: '👉 [แชร์ให้เว็บไซต์]', type:'mdi-alpha-x', web: 'mdi-circle-outline' , tv: 1, sms:'mdi-circle-outline', smsflash: 'mdi-circle-outline', pr:'mdi-circle-outline',  date: '22/09/2567'},
        { group: 'ทั่วไทย', title: 'ฮือฮาสร้างเสียงรอยยิ้ม !!! รองผู้การแต่งชุดตำรวขจโบก...', status: '👉 [แชร์ให้เว็บไซต์และทีวี]', type:'mdi-alpha-x', web: 'mdi-circle-outline' , tv: '', sms:'mdi-circle-outline', smsflash: 'mdi-circle-outline', pr:'mdi-circle-outline',  date: '22/09/2567'},
        { group: 'ทีวี', title: 'คนดั้งเดิมชาวจันทรบุรีและใกล้เคียง แข่งประชันเสียง...', status: '👉 [แชร์ให้ทีวี]', type:'mdi-alpha-x', web: 'mdi-circle-outline' , tv: '', sms:'mdi-circle-outline', smsflash: 'mdi-circle-outline', pr:'mdi-circle-outline',  date: '22/09/2567'},
        { group: 'บันเทิง', title: 'บิดสุดเพื่อหลบน้อง !!  ชาวบ้านบิดมอเตอร์ไซต์ลงคลองข้างทาง คาดเพื่อหลบสุนัข...', status: '👉 [แชร์ให้เว็บไซต์]', type:'mdi-alpha-x', web: 'mdi-circle-outline' , tv: 1, sms:'mdi-circle-outline', smsflash: 'mdi-circle-outline', pr:'mdi-circle-outline',  date: '22/09/2567'},
      ],
      search: '',
      serverItems: [],
      loading: false,
      totalItems: 0,
    }),
    methods: {
    },
  }
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Kanit:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');
*, .text-subtitle-1.text-medium-emphasis.mt-n1{
  font-family: "Kanit", sans-serif;
  font-style: normal;
}
</style>


