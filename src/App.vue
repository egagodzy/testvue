<template>
    <div class="w-[1920px] h-[1024px]">
        <div id="PageName" class="pl-[481px] pt-[204px]">
            <a class="font-['TT Norms'] text-[40px] leading-[48px]">Города</a>
        </div>
        <div class="w-[960px] h-[455px] pt-[28px] mx-auto my-auto]">
            <div id="CitySearch" class="flex h-[58px]">
                <div class="bg-[#F6F7F7] flex border rounded-lg border-[#E1E1E1]">
                    <img src="./assets/si.png" class="w-[24px] h-[24px] mx-auto my-auto">
                    <input type="text" v-model="searchQuery" class="bg-[#F6F7F7] w-[958px] text-[18px] pl-[25px]" placeholder="Поиск по городу">
                </div>
            </div>
            <div class="" v-for="opa in letters">
                <div class="pt-[10px]">
                    <strong class="font-['TT Norms'] h-[24px] text-[18px] leading-[24px]">{{ opa }}</strong>
                </div>
                <div id="Letters" class="inline-flex" v-for="got in SearchCity">
                    <div id="Citys" class="pt-[10px]" v-if="got[0] === opa">
                        <div class="w-[300px] flex justify-center h-[24px] text-[18px] leading-[24px]">
                            <p>{{ got }}</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>       
</template>

<script>
export default {
    data() {
        return {
            letters: [
                'А', 'Б', 'В', 'Г', 'Д', 'Е', 'Ё', 'Ж', 'З', 'И', 'Й', 'К', 'Л', 'М', 'Н',
                'О', 'П', 'Р', 'С', 'Т', 'У', 'Ф', 'Х', 'Ц', 'Ч', 'Ш', 'Щ', 'Ъ', 'Ы', 'Ь',
                'Э', 'Ю', 'Я'
            ],
            citys: [],
            searchQuery: '',
        }
    },
    methods: {
        async FetchData() {
            const ksjs = require('./jsjs/entities.json');
            for (let i = 0; i < ksjs.length; i += 1) {
                this.citys.push(ksjs[i].name)
            };  
        }
    },
    mounted() {
        this.FetchData();
    },
    computed: {
        SearchCity() {
            return this.citys.filter(go => go.toLowerCase().includes(this.searchQuery.toLowerCase()))
        }
    },
}

</script>

<style>
    
</style>