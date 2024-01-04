<script>
export default {
    data() {
        return {
            picFile: '',
            filePic: '',
        }
    },
    methods: {
        uploadPic(event) {
            // console.log(event);
            this.picFile = event.target.file[0];
            console.log(this.picFile);
            if (this.picFile) {
                const reader = new FileReader();
                reader.readAsDataURL(this.picFile);
                reader.onload = (e) => {
                    console.log(e);
                    this.filePic = e.target.result;
                    this.imageFile = [
                        {
                            name: this.picFile.name,
                            path: this.filePic,
                        }
                    ];
                };
            }
        }
    }
}
</script>

<template>
    <div>
        <input type="file" accept=".jpg,.png" @change="uploadPic()">
    </div>
    <div class="my-3">
        <button type="button" class="border-2 rounded-lg px-2 py-1">上傳圖片</button>˝
    </div>
</template>

<style></style>