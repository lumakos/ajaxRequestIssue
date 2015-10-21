# ajax Request Issue

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
