<template>
<div class="register">
<form @submit.prevent="register">
<h2>新規登録</h2>
<input type="text" placeholder="ユーザーネーム" v-model="name">
<input type="email" placeholder="メールアドレス" v-model="email">
<input type="password" placeholder="パスワード v-model="password">
<button type="submit">登録する</button>
</form>
</div>
</template>

<script>
export default {
data() {
return {
name: null,
email: null,
password: null,
};
},
methods: {
async register() {
try {
await this.$axios.post("http://localhost:8000/api/auth/register", {
name: this.name,
email: this.email,
password: this.password,
});
this.$router.push("/login");
} catch {
alert("メールアドレスがすでに登録されています");
}
},
},
};
</script>
