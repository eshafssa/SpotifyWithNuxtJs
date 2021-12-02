<template>
<div class="bg-dark  h-screen">
  <div class="flex relative  h-full ">

    <!-- sidebar -->
    <div class="bg-yellow-400  w-60 h-full flex-none sticky">


    </div>
    <!-- content -->
    <div class="bg-red-400   h-full w-full text-white overflow-auto ">
      <!-- menu -->
      <div class="bg-green-400 sticky  top-0 h-15 z-20">

      </div>
        <!-- content -->

        <!-- Recently played cards -->

        <!-- Daily mix  cards -->



    </div>
    <div class="bg-blue-400" style="height:12vh;"></div>

  </div>
</div>
</template>

<script>
import MyIcons from '~/components/MyIcons.vue'
import { mixin as clickaway} from 'vue-clickaway'


export default {
  components: { MyIcons },
  mixins:[clickaway],

  data :function(){
    return{
      setId:'home',
      ShowDropdown:false,

      pages:[
        {id:'home',name:'Home',icon:'home'},
        {id:'search',name:'Search',icon:'search'},
        {id:'library',name:'Your library',icon:'library'}
      ],
      albums:[
        {name:'album 1'},
        {name:'album 2'},
        {name:'album 3'},
        {name:'album 4'},
        {name:'album 5'},
        {name:'album 6'},

      ],
      recents:[
        {id:1,image:'image1.png',title1:'AWAWAWA',          title2:'lzzl Vibes'},
        {id:2,image:'image2.png',title1:'Arabic Love Songs',title2:'To all 7abieb out there,Cover:Nancy Ajram'},
        {id:3,image:'image33.png',title1:'Nharek Zin',      title2:'Passez une bonne journée en musique'},
        {id:4,image:'image4.png',title1:'Urban Arab Pop',   title2:'Middle Eastern and North African Heat. Cover:Ouenza'},
        {id:5,image:'image5.png',title1:'Alone Again',      title2:'Being alone (again) can be though'},
        {id:6,image:'image6.png',title1:'Feelin\' Myself',  title2:''}
      ],
      daylies:[
        {id:1,image:'daily1.png',title1:'Daily Mix 1', title2:'Tagne,Manal,Ihan snd more'},
        {id:2,image:'daily2.png',title1:'Daily Mix 2', title2:'Zouhair Bahaoui,Zina,MIYA and more'},
        {id:3,image:'daily3.png',title1:'Daily Mix 3', title2:'Anson Seebra, Lewis Capaldi,Bilie Eilish and more'},
        {id:4,image:'daily4.png',title1:'Daily Mix 4', title2:'Ramy Sbry, Amr Diab and more'},
        {id:5,image:'daily5.png',title1:'Daily Mix 5', title2:'Ragheb alam,George wwassouf, Ghalia and more'},
        {id:6,image:'daily6.png',title1:'Daily Mix 6', title2:'Ziad Bourji, Nancy Ajram,Nina Abdelmalek'}
      ]
    }
  },
   methods:{
    away:function(){
     this.ShowDropdown= false
    },
  },
}

</script>
<style >
::-webkit-scrollbar{
  width: 6px;
}
::-webkit-scrollbar-thumb{
  background: gray;
  border-radius: 20%;
}
</style>
