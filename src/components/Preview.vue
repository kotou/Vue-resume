<template>
    <div id="preview">
        <h1>{{resume.profile.name || '请填写姓名'}}</h1>
        <p>{{resume.profile.city || '请填写城市'}} | {{resume.profile.birth || '请填写出生年月'}}</p>
        <hr>
        <section v-if="filter(resume.studyExperience).length > 0">
            <h2>学习经历</h2>
            <ul>
                <li v-for="study in filter(resume.studyExperience)">
                    {{study.school}} {{study.duration}} {{study.degree}}
                </li>
            </ul>
        </section>
        <section v-if="filter(resume.workExperience).length > 0">
            <h2>工作经验</h2>
            <ul>
                <li v-for="wrok in filter(resume.workExperience)">
                    {{wrok.company}} {{wrok.content}}
                </li>
            </ul>
        </section>
        <section v-if="filter(resume.projects).length > 0">
            <h2>项目</h2>
            <ul>
                <li v-for="project in filter(resume.projects)">
                    {{project.name}} {{project.content}}
                </li>
            </ul>
        </section>
        <section v-if="filter(resume.awards).length > 0">
            <h2>获奖情况</h2>
            <ul>
                <li v-for="award in filter(resume.awards)">
                    {{award.name}}
                </li>
            </ul>
        </section>
        <section>
            <h2>联系方式</h2>
            <p>{{resume.contacts.qq}} {{resume.contacts.wechat}} {{resume.contacts.email}} {{resume.contacts.phone}}</p>
        </section>
    </div>
</template>
<script>
    export default {
        props: ['resume'],
        methods: {
            filter(array) {
                return array.filter(item => !this.isEmpty(item))
            },
            isEmpty(object) {
                let empty = true
                for (let key in object) {
                    if (object[key]) {
                        empty = false
                        break
                    }
                }
                return empty
            }
        }
    }
</script>
<style lang='scss'>
</style>