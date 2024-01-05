<script>
export default {
    data() {
        return {
            imageFile: '',
            filePic: '',
            fileInfo: [],
        }
    },
    methods: {
        uploadPic(event) {
            this.imageFile = event.target.files[0];
            // console.log(this.imageFile);
            if (this.imageFile) {
                const reader = new FileReader();
                reader.readAsDataURL(this.imageFile);
                reader.onload = (e) => {
                    console.log(e);
                    this.filePic = e.target.result;
                    this.fileInfo = [
                        {
                            name: this.imageFile.name,
                            path: this.filePic,
                        }

                    ];
                    // console.log(this.fileInfo);
                }
            }
        },
        submit() {
            this.fileInfo
        }

    },
};
</script>

<template>
    <div class="my-2">
        <input type="file" accept=".jpg,.png" @change="uploadPic">
    </div>
    <div class="w-[500px]">
        <img :src="filePic" alt="" class="object-cover">
    </div>
    <div class="inline-block border-2 rounded-lg px-2 py-1 mt-2">
        <button type="button" @click="submit()">上傳圖片</button>
    </div>
</template>

<style></style>