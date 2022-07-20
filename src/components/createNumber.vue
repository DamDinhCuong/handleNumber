<template>
    <div class="row">
        <form action="">
            <div class="col-sm-8 form-group ml-250">
                <input placeholder="Nhập vào dãy số" v-model="items" type="text">
            </div>
            <div class="col-sm-8 form-group btn-container ml-250">
                <button @click.prevent ="TangNumber" type="button" class="btn btn-outline-success">Tăng</button>
                <button @click.prevent ="GiamNumber" type="button" class="btn btn-outline-success">Giảm</button>
                <button @click.prevent ="XoaSoChan" type="button" class="btn btn-outline-success">Xóa số chẵn</button>
                <button @click.prevent ="XoaSoLe" type="button" class="btn btn-outline-success">Xóa số lẻ</button>
                <button @click.prevent ="TongCacSo" type="button" class="btn btn-outline-success">Tổng</button>

            </div>

        </form>
    </div>
</template>

<script>
export default {
    data: function() {
        return {
            myArr: [],
            items: '',
            sum: 0,
        }
    },

    methods: {

        clearForm() {
            this.myArr = [];
            this.sum = 0;
        },

        TangNumber() {
            const value = this.items;
            if(value.length > 0) {
                for(var i = 0; i < value.length; i++) {
                    if(isNaN(value[i]) || value[i] == ' ') {
                        alert("Vui lòng nhập tất cả là số và không có khoảng trắng!!!")
                        return this.clearForm()
                    }
                    else {
                        this.myArr.push(Number(value[i]));
                    }
                }
                this.$emit('itemAdded', this.myArr.sort());
                this.clearForm()
            }
        },

        GiamNumber() {
            const value = this.items;
            if(value.length > 0) {
                for(var i = 0; i < value.length; i++) {
                 if(isNaN(value[i]) || value[i] == ' ') {
                        alert("Vui lòng nhập tất cả là số và không có khoảng trắng!!!")
                        return this.clearForm()
                    }
                    else {
                        this.myArr.push(Number(value[i]));
                    }
            }
                this.$emit('itemAdded', this.myArr.sort().reverse());
                this.clearForm()
            }
            
        },

        TongCacSo() {
            const value = this.items;
            if(value.length > 0) {
                for(var i = 0; i < value.length; i++) {
                 if(isNaN(value[i]) || value[i] == ' ') {
                        alert("Vui lòng nhập tất cả là số và không có khoảng trắng!!!")
                        return this.clearForm()
                    }
                    else {
                        this.sum+= Number(value[i]);
                        
                    }
            }
                this.$emit('itemAdded', this.sum);
                this.clearForm()
            }
        },

        XoaSoChan() {
            const value = this.items;
            if(value.length > 0) {
                for(var i = 0; i < value.length; i++) {
                    if(isNaN(value[i]) || value[i] == ' ') {
                        alert("Vui lòng nhập tất cả là số và không có khoảng trắng!!!")
                        return this.clearForm()
                    }
                    else {
                        this.myArr.push(Number(value[i]));
                    }
                }
                this.$emit('itemAdded', this.myArr.filter(item => item % 2 !== 0));
                this.clearForm()
            }
        },

        XoaSoLe() {
            const value = this.items;
            if(value.length > 0) {
                for(var i = 0; i < value.length; i++) {
                    if(isNaN(value[i]) || value[i] == ' ') {
                        alert("Vui lòng nhập tất cả là số và không có khoảng trắng!!!")
                        return this.clearForm()
                    }
                    else {
                        this.myArr.push(Number(value[i]));
                    }
                }
                this.$emit('itemAdded', this.myArr.filter(item => item % 2 === 0));
                this.clearForm()
            }
        },
        
    }
}
</script>

<style>
    form {
        width: 100%;
        margin-top: 150px;
    }
    .btn {
        margin: 8px;
        border: 2px solid #000;
        color: #000;
    }

    .ml-250 {
        margin-left: 250px;
    }

    .form-group {
        text-align: center;
    }
</style>
