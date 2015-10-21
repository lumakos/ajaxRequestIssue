# ajax Request Issue
Let's talk about the case that we have a javascript script that execute with the ajax request.
The problem: While executing javascript code a new same ajax request appears about the same object ,so code should executed again for the last ajax and maybe create problems like fire a modal again etc.
The solution: we create a backup of the origin ajax request , we compare the backup with the new request and we push the differences in the origin.


var notificationsArray = jQuery.parseJSON(json);
var testingNotificationsArray = jQuery.parseJSON(json);
    for(var key in testingNotificationsArray) {
        if(testingNotificationsArray.hasOwnProperty(key)) {
            for (var i=0; i<testingNotificationsArray[key].length; i++) {
                var new_not = testingNotificationsArray[key][i].id;
                var check = true;

                for(var x=0; x<notificationsArray[key].length; x++){
                    var old = notificationsArray[key][x].id;
                    if( new_not === old) {
                        check = false;
                        break;
                    }
                }
                if(check === true){
                    notificationsArray[key].push(testingNotificationsArray[key][i]);
                }
            }
        }
    }
