<template>
  <div id="app" class="container">
    <messages></messages>
    <auth></auth>
    <add-modal></add-modal>
    <navbar></navbar>
    <router-view/>

    <div id="donate-btn" class="ws-add">
      <p>Help keep the lights on. </p>&nbsp;
      <form action="https://www.paypal.com/cgi-bin/webscr" method="post" target="_top">
        <input type="hidden" name="cmd" value="_s-xclick" />
        <input type="hidden" name="hosted_button_id" value="WX5KZWZ6DRYVU" />
        <input type="image" src="https://www.paypalobjects.com/en_US/i/btn/btn_donate_SM.gif" border="0" name="submit" title="PayPal - The safer, easier way to pay online!" alt="Donate with PayPal button" />
        <img alt="" border="0" src="https://www.paypal.com/en_US/i/scr/pixel.gif" width="1" height="1" />
      </form>
      <p>Thank you!</p>
    </div>
    <div id="about-dev" class="ws-add">
      <p>Hire <a href="https://github.com/duncannevin" target="_blank">Duncan Nevin</a> for your next project.</p>
    </div>
  </div>
</template>

<script>
import Navbar from './components/Navbar'
import {makeResizable} from './utils'
import AddModal from './components/AddModal'
import Auth from './components/Auth'
import Messages from './components/Messages'
export default {
  name: 'App',
  mounted () {
    makeResizable()
    this.$store.dispatch('init')
  },
  components: {
    Messages,
    Navbar,
    AddModal,
    Auth
  }
}
</script>

<style lang="sass">
@import '../../node_modules/bootstrap/scss/bootstrap.scss'
@import '../../node_modules/bootstrap-vue/dist/bootstrap-vue.css'
@import './styles/normalize.sass'
@import './styles/custom-bootstrap.sass'
@import './styles/variables.sass'
@import './styles/editor'
body
  background: $black
  font-family: $font-family-monospace
  height: 100%
  overflow: auto
.container-fluid
  padding-left: 0
  padding-right: 0
.section
  display: flex
  margin: 1rem 0
  div
    padding: 0
  .control-buttons
    display: flex
    flex-direction: column
    justify-content: space-between
.col
  padding: 0
.row
  margin-right: 0
  margin-left: 0
.ace_editor
  resize: vertical
.ace_content
  padding-bottom: 100px
.ace_scrollbar
  display: none
.form-control:disabled
  opacity: 0.8
.disabled:hover
  cursor: not-allowed
.delete-button
  color: $red
.modal-content
  background-color: $black
  color: $white
.add-icon:hover
  cursor: pointer
.text-muted
  color: $gray-light!important
.add-icon
  font-size: 1.5rem
  color: $white
.nav-link .add-icon
  transform: translateY(-0.25rem)
.display
  position: relative
  height: 200px
  min-height: 100px
  width: 100%
  border-bottom: 3px solid $green
  .display-title
    position: absolute
    bottom: 0
    font-size: 0.85rem
    left: 30px
    color: $green
.nav-tabs
  border-bottom: none
  .nav-item
    .nav-link
      color: $white
      background-color: transparent
      border: none
      padding: 0
      margin-right: 1rem
    .nav-link.active
      color: $green
      border-bottom: 3px solid $green
.section-controls
  position: absolute
  top: 0
  right: 0
  .show > .btn-secondary.dropdown-toggle
    background-color: transparent
    border: none
  .btn
    font-size: 1rem
    font-weight: bold
    padding: 0 0 0 1rem
    height: min-content
    background-color: transparent
    border: none
  .btn:focus
    box-shadow: none
.animated
  animation-duration: 1s
  animation-fill-mode: both

@keyframes zoomIn
  from
    opacity: 0
    transform: scale3d(0.3, 0.3, 0.3)

  50%
    opacity: 1

.zoomIn
  animation-name: zoomIn

@keyframes blink
  50%
    color: transparent
.loader-dot
  animation: 1s blink infinite
.loader-dot:nth-child(2)
  animation-delay: 250ms
.loader-dot:nth-child(3)
  animation-delay: 500ms

.ws-add
  display: flex
  color: $green
  position: fixed
  padding: 0 1rem
#donate-btn
  bottom: 0
  left: 0
#about-dev
  flex-direction: column
  bottom: 0
  right: 0
  padding-bottom: 0.75rem
  p
    margin: 0
</style>
