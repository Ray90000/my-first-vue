<script>
export default {
    data() {
        return {
            picFile: '',
            filePic: '',
            imageFile:[],
        }
    },
    methods: {
        uploadPic(e) {
            console.log(e);
            this.picFile = e.target.files[0];
            console.log(this.picFile);
            if(this.picFile){
                const reader = new FileReader();
                reader.readAsDataURL(this.picFile);
                reader.onload = (e) => {
                    console.log(e);
                    this.filePic = e.target.result;
                    this.imageFile = [
                        {
                            name:this.picFile.name,
                        }
                    ]
                }
            }
        }
    },
}
</script>
<template>
    <input type="file" accept=".jpg, .png" @change="uploadPic">
    <img :src="filePic" alt="">
    <button type="button">上傳圖片</button>
    
</template>
<style></style>