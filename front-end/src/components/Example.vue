<script>
    import IconBase from './IconBase'
    import IconRetweet from './icons/IconRetweet'
    import IconSpeech from './icons/IconSpeech'
    import IconClose from './icons/IconClose'
    import IconLike from './icons/IconLike'
    import { HTTP } from '../utils/api'
    import debounce from '../debounce.js'
    export default {
        name: 'TwitterPost',
        props: {
            post: Object
        },
        data () {
            return {
                counterLikes: 0,
                counterSpeech: 0,
                counterRetweet: 0,
                showModal: false,
                numberCommentsOfPost: []
            }
        },
        components: {
            IconBase,
            IconRetweet,
            IconSpeech,
            IconLike,
            IconClose
        },
        mounted () {
            HTTP.get('/comments')
                .then((response) => {
                    let commNumb = this.post.id
                    this.counterSpeech = response.data.filter(el => el.postId === commNumb).length
                })
        },
        computed: {
            debouncedSave: function () {
                let DELAY = 1000
                return debounce(this.increaseLikesPost, DELAY)
            },
            classObject: function () {
                return this.$store.getters.isDarkModed ? 'dark' : 'light'
            }
        },
        methods: {
            deleteTheVeryPost: function () {
                HTTP.delete('/posts/' + this.post.id)
                    .then(response => {})
                    .catch(error => console.log(error))
                this.commentMessage = ''
                this.$emit('delete-post', this.post.id)
            },
            increaseLikesPost: function () {
                let lk = this.post.likes + 1
                HTTP.patch(('/posts/' + this.post.id), {
                    'likes': lk
                }).then(response => {})
                    .catch(error => console.log(error))
                this.$emit('re-like-post', this.post.id)
            }
        }
    }
</script>