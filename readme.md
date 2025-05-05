# Vue Lifecyle
## [What is Lifecyle in Vue?](https://vuejs.org/guide/essentials/lifecycle.html#lifecycle-hooks)
Lifecyle dalam vue adalah rangkaian dari tahapan yang dilalui oleh sebuah komponen Vue dari saat ia dibuat hingga saat ia dihapus. Setiap tahapan ini memiliki event-event tertentu yang dapat kita gunakan untuk menjalankan kode pada saat komponen berada pada tahapan tersebut. Dengan memahami lifecyle, kita dapat mengoptimalkan performa aplikasi dan mengelola state dengan lebih baik.

## [Lifecyle in Vue](https://learnvue.co/articles/vue-lifecycle-hooks-guide)
Tahapan lifecyle dalam Vue terdiri dari beberapa fase, yaitu:
1. **Creation**: Fase ini dimulai saat komponen dibuat. Pada fase ini, kita dapat melakukan inisialisasi data, mengatur props, dan melakukan setup lainnya.
2. **Mounting**: Fase ini terjadi saat komponen ditambahkan ke DOM. Pada fase ini, kita dapat melakukan manipulasi DOM dan mengatur event listener.
3. **Updating**: Fase ini terjadi saat data pada komponen berubah. Pada fase ini, kita dapat melakukan pembaruan pada tampilan komponen sesuai dengan perubahan data.
4. **Destruction**: Fase ini terjadi saat komponen dihapus dari DOM. Pada fase ini, kita dapat membersihkan event listener dan melakukan pembersihan lainnya.


## [Lifecyle Hooks](https://vuejs.org/guide/essentials/lifecycle.html#lifecycle-hooks)
Untuk mengelola tahapan lifecyle, Vue menyediakan beberapa lifecycle hooks yang dapat kita gunakan. Berikut adalah beberapa lifecycle hooks yang sering digunakan:

| Option API | Composition API | Description |
|------------|----------------|-------------|
| [beforeCreate](https://vuejs.org/api/options-lifecycle.html#beforecreate) | [setup()](https://vuejs.org/api/composition-api-setup.html#composition-api-setup) | Terjadi sebelum terbentuknya reactive data dan komponen |
| [created](https://vuejs.org/api/options-lifecycle.html#created) | [setup()](https://vuejs.org/api/composition-api-setup.html#composition-api-setup) | Terjadi setelah terbentuknya reactive data dan komponen  |
| [beforeMount](https://vuejs.org/api/options-lifecycle.html#beforemount) | [onBeforeMount()](https://vuejs.org/api/composition-api-lifecycle.html#onbeforemount) | Terjadi sebelum komponen ter-mounted di dalam DOM |
| [mounted](https://vuejs.org/api/options-lifecycle.html#mounted    ) | [onMounted()](https://vuejs.org/api/composition-api-lifecycle.html#onmounted) | Terjadi setelah komponen ter-mounted di dalam DOM |
| [beforeUpdate](https://vuejs.org/api/options-lifecycle.html#beforeupdate) | [onBeforeUpdate()](https://vuejs.org/api/composition-api-lifecycle.html#onbeforeupdate) | Terjadi setelah adanya perubahan data dan sebelum komponen ter-render ulang |
| [updated](https://vuejs.org/api/options-lifecycle.html#updated) | [onUpdated()](https://vuejs.org/api/composition-api-lifecycle.html#onupdated) | Terjadi setelah komponen ter-render ulang |
| [beforeUnmount](https://vuejs.org/api/options-lifecycle.html#beforeunmount) | [onBeforeUnmount()](https://vuejs.org/api/composition-api-lifecycle.html#onbeforeunmount) | Terjadi sebelum komponen di-unmount dari DOM |
| [unmounted](https://vuejs.org/api/options-lifecycle.html#unmounted) | [onUnmounted()](https://vuejs.org/api/composition-api-lifecycle.html#onunmounted) | Terjadi setelah komponen di-unmount dari DOM |

## Demo 
Untuk demo kali ini kita akan menggunakan [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) untuk fetching data dari [Dummyjson.com](https://dummyjson.com/docs/products#products-all) untuk mendapatkan data produk. Nah bagaimana cara kita mendapatkan datanya sebelum halaman di-render? Kita bisa menggunakan lifecycle hooks `created` pada Option API atau `setup` pada Composition API.