# WPLMS-Popup-Free-Unit
###### Open Popup when user try to see free units
This code works when the users try to enter to see free units.

1.-Add this code in WPLMS customizer plugin ("wplms-customizer.php")

```
add_filter('wplms_curriculum_course_lesson','wplms_free_access_2',99,3);
function wplms_free_access_2($html,$lesson,$course_id){
if(!is_user_logged_in()){
$free=get_post_meta($lesson,'vibe_free',true);
return '<a class="button_trig_login" href="#">'.get_the_title($lesson).(vibe_validate($free)?'<span>'.__('Gratuit','wplms_modern').'</span>':'').'</a>';
}else{
return $html;
}
}
```
2.-Now add this code in your wplms -> footer -> google anaylitics :
```
<script>
jQuery("document").ready(function($){
$(".button_trig_login").on('click',function(event){
event.preventDefault();
$('a.smallimg.vbplogin').trigger('click');
});
});
</script>
```

For more reference:
http://vibethemes.com/documentation/wplms/knowledge-base/restricting-non-logged-in-user-to-see-the-free-unit/
http://vibethemes.com/documentation/wplms/forums/topic/button-to-open-the-login-popup-of-default-theme/
http://vibethemes.com/documentation/wplms/knowledge-base/open-login-popup-on-free-course-login-error/
