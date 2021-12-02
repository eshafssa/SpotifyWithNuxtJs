<template>
<div class="bg-dark  h-screen ">
  <div class="flex relative bg-dark   h-full " style="height:88vh;">

    <!-- sidebar -->
    <div class="bg-black  w-60 h-full flex-none sticky">
      <div class="p-6">
         <img src="~/assets/img/SpotifyLogoWhite.png"  alt="spotify" class="h-10">
      </div>
      <!-- items -->
      <div v-for="page in pages" :key="(index,page.id)" class="mx-1 ">
        <button @click="setId=page.id" :class="`hover:text-white w-full px-6 py-2 rounded-lg items-center  font-semibold text-md ${setId===page.id ? 'bg-light text-white':'text-lightest'} `">
          <p class="flex">
            <my-icons :name="page.icon" class="w-6 h-6 mr-6"></my-icons>
            {{page.name}}
          </p>
        </button>
      </div>
      <div class="">
        <p class="uppercase text-lightest  tracking-widest  px-9 py-6">playlists</p>
       <div class="mx-8">
         <button class="flex  pb-6 text-lightest opacity-75 hover:opacity-100">
            <img src="~/assets/img/addNew.png" alt="" class="w-6 h-6 mr-6">
            <h2 class="items-center font-semibold">Create Playlist</h2>
          </button>
          <button class="flex pb-6 text-lightest opacity-75 hover:opacity-100">
            <img src="~/assets/img/myFavorite.png" alt="" class="w-6 h-6 mr-6">
            <h2 class="flex items-center justify-center font-semibold">Liked Songs</h2>
          </button>
        <div class="bg-light h-px w-full my-3"> </div>
       </div>
       <div class="mx-8 h-10 m-3  overflow-y-scroll" style="webkit: scroll;">
         <div v-for="album in albums" :key="(album.id)" class="pt-2">
           <p class="text-lightest font-semibold capitalize text-sm hover:text-white ">{{album.name}}</p>
         </div>
       </div>
       <div class="flex mx-8 text-lightest items-center  font-semibold text-ms hover:text-white ">
         <my-icons name="download" class="pr-3"></my-icons>
         <button class="">Install app</button>
       </div>
       <div class="pt-5 relative">
         <div class="h-full w-full flex  justify-end items-start opacity-0 hover:opacity-100 absolute p-2">
           <div class="bg-black rounded-full h-6 w-6 opacity-50">
               <my-icons name="down" class="text-lightest"></my-icons>
           </div>
         </div>
         <img src="~/assets/img/album.png" alt="" class="">
       </div>
      </div>
    </div>
    <!-- content -->
    <div class="bg-dark   h-full w-full text-white overflow-auto ">
      <!-- header -->
      <div class="bg-dark sticky  top-0 h-15 z-20">
        <div class="flex items-center justify-between">
          <div class="my-5 mx-5">
            <button class="bg-light rounded-full  w-8 h-8 mr-3">
              <my-icons name="left" class="text-lightest opacity-100"></my-icons>
            </button>
            <button class="bg-light rounded-full  w-8 h-8 ">
              <my-icons name="right" class="text-lightest opacity-100"></my-icons>
            </button>
         </div>
         <div class="mx-5 relative">
            <button @click="ShowDropdown = true"  class="flex h-9 bg-light rounded-full items-center">
              <img src="~/assets/img/userr.png" alt="" class="w-8 h-8 rounded-full mr-3 ml-1">
              <p class="text-white  mr-3 text-sm font-semibold">Username</p>
              <my-icons v-if="ShowDropdown === false" name="down" class="mr-2"></my-icons>
              <my-icons v-else-if="ShowDropdown === true" name="up" class="mr-2"></my-icons>
            </button>
           <div v-if="ShowDropdown === true" v-on-clickaway="away"  class="absolute bg-light w-full mt-1">
              <button class="p-2 text-lightest text-sm font-semibold w-full hover:bg-mygray"> Account </button>
              <button class="p-2 text-lightest text-sm font-semibold w-full hover:bg-mygray"> Profile </button>
              <button class="p-2 text-lightest text-sm font-semibold w-full hover:bg-mygray border-b  border-gray-500 "> Settings </button>
              <button class="p-2 text-lightest text-sm font-semibold w-full hover:bg-mygray"> Log out </button>
           </div>
         </div>

        </div>
      </div>
        <!-- content -->

        <!-- Recently played cards -->
        <div class="px-4 py-3">
            <div class="flex items-center justify-between mt-4">
              <h1 class="pl-2 text-white font-semibold  text-2xl tracking-wider hover:underline mt-5 cursor-pointer">Recently played</h1>
              <h1 class="pr-8 pt-4 text-lightest font-semibold text-xs tracking-wider hover:underline mt-5 cursor-pointer">SEE ALL</h1>
            </div>
          <div class="w-full flex flex-wrap mt-5 ">
            <div v-for="recent in recents" :key="recent.id" class="p-2 w-48 relative z-10">
              <div class="bg-light w-full h-64 p-5 rounded-lg shadow-md hover:bg-mygray cursor-pointer">
                 <img :src="`img/${recent.image }`" class="h-auto w-full shadow mb-2">
                <h1 class="text-white text-sm font-semibold tracking-wide pb-1">{{recent.title1}}</h1>
                <h2 class="text-lightest text-xs  tracking-wide ">{{recent.title2}}</h2>
              </div>
              <div class="absolute w-full h-full opacity-0 hover:opacity-100 top-0 cursor-pointer">
                <div class="flex justify-end h-full items-center">
                  <my-icons name="play" class="bg-mygreen p-1.5 rounded-full m-10 shadow transition"></my-icons>
                </div>
              </div>
            </div>

          </div>
        </div>
        <!-- Daily mix  cards -->
        <div class="px-4 py-3 ">
          <div class="flex items-center justify-between">
            <h1 class="pl-2 text-white font-semibold text-2xl hover:underline tracking-wide cursor-pointer">Made For Eshafssa</h1>
            <h2 class="pr-8 pt-4 text-lightest font-semibold text-xs hover:underline cursor-pointer">SEE ALL</h2>
          </div>
          <h2 class="pl-2 text-lightest font-semibold text-sm">Get better recommendations the more you listen.</h2>
          <div class="flex w-full flex-wrap mt-5  ">
            <div v-for="daylie in daylies" :key="daylie.id" class="w-48 p-2 relative ">
              <div  class=" bg-light w-full h-64 p-5 rounded-lg shadow-md hover:bg-mygray cursor-pointer  ">
                  <img :src="`img/${daylie.image}`" alt="" class="shadow h-auto w-full mb-2 ">
                  <h1 class="text-white text-sm font-semibold tracking-wide pb-1">{{daylie.title1}}</h1>
                  <h2 class="text-lightest text-xs  tracking-wide">{{daylie.title2}}</h2>
              </div>
              <div class="absolute w-full h-full opacity-0 hover:opacity-100 top-0 cursor-pointer">
                <div class="flex justify-end h-full items-center">
                  <my-icons name="play" class="bg-mygreen p-1.5 rounded-full m-10 shadow transition"></my-icons>
                </div>
              </div>
            </div>
          </div>
        </div>
            <!-- Made for Eshafssa cards -->
        <div class="px-4 py-3 ">
          <div class="flex items-center justify-between">
            <h1 class="pl-2 text-white font-semibold text-2xl hover:underline tracking-wide cursor-pointer">Made For Eshafssa</h1>
            <h2 class="pr-8 pt-4 text-lightest font-semibold text-xs hover:underline cursor-pointer">SEE ALL</h2>
          </div>
          <h2 class="pl-2 text-lightest font-semibold text-sm">Get better recommendations the more you listen.</h2>
          <div class="flex w-full flex-wrap mt-5  ">
            <div v-for="recent in recents" :key="recent.id" class="w-48 p-2 relative">
              <div  class=" bg-light w-full h-64 p-5 rounded-lg shadow-md hover:bg-mygray cursor-pointer  ">
                  <img :src="`img/${recent.image}`" alt="" class="shadow h-auto w-full mb-2 ">
                  <h1 class="text-white text-sm font-semibold tracking-wide pb-1">{{recent.title1}}</h1>
                  <h2 class="text-lightest text-xs  tracking-wide">{{recent.title2}}</h2>
              </div>
              <div class="absolute w-full h-full opacity-0 hover:opacity-100 top-0 cursor-pointer">
                <div class="flex justify-end h-full items-center">
                  <my-icons name="play" class="bg-mygreen p-1.5 rounded-full m-10 shadow transition"></my-icons>
                </div>
              </div>
            </div>
          </div>
        </div>
    </div>
  </div>
  <div class="w-full px-3 flex items-center  justify-between bg-darkest" style="height:12vh;">
    <div class="flex items-center ">
      <div >
        <h1 class="text-white text-md font-semibold ">Lovely (with khalid)</h1>
        <h2 class="text-lightest text-sm font-semibold">Billie Eilish,Khalid</h2>
      </div>
      <my-icons name="favorite" class="text-lightest mx-4"></my-icons>
      <my-icons name="picinpic" class="text-lightest"></my-icons>
    </div>
    <div class="w-2/5">
      <div class="flex items-center justify-center">
        <button class="text-lightest mx-4 hover:text-white"><my-icons name="shuffle"></my-icons></button>
        <button class="text-lightest mx-2 hover:text-white"><my-icons name="skipback"></my-icons></button>
        <button @click.prevent="playSongs('lovely.mp3') ,playS = !playS" class="text-lightest mx-2 hover:text-white">
          <my-icons v-if="playS===false" name="playCircle"></my-icons>
          <my-icons v-else-if="playS===true" name="pauseCircle"></my-icons>
        </button>
        <button class="text-lightest mx-2 hover:text-white"><my-icons name="skipNext"></my-icons></button>
        <button class="text-lightest mx-4 hover:text-white"><my-icons name="repeat"></my-icons></button>
      </div>
      <div class="flex items-center justify-center mt-2 ">
        <h2 class="text-lightest mx-2 flex items-center">1:20</h2>
        <div class="bg-light  w-full h-1 rounded-full">
          <div class="bg-mygreen h-1 rounded-full flex items-center justify-center" style="width: 190px;">
             <div class=" rounded-full bg-white h-3  w-3  ml-44"></div>
            </div>
        </div>
        <h2 class="text-lightest  mx-2 flex items-center">3:20</h2>
      </div>
    </div>

    <div class="flex items-center">
      <my-icons name="playlist" class="text-lightest mx-4"></my-icons>
      <my-icons name="screen" class="text-lightest mr-4"></my-icons>
      <my-icons name="volume" class="text-lightest mr-2"></my-icons>
      <div class=" w-24 bg-lightest h-1 rounded-full "></div>
    </div>
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
      playS:false,
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
    playSongs(song){
      if(song){
      	var audio = new Audio (song);
        audio.play();
      }
    }
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
