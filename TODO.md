1. Looks like you need to ignore duplicates for now in the array. Might have to wait until you have a database in place to deal with this issue.

2. Using writable store to save information:

// const addToArray = (lift, weight) => {
        // validate that a number was entered for weight
        // if (!isNaN(weight)) {
            // window.alert(`${writableArray.length}`)

            // check to see if lift already exists and make sure new weight is not less than previous entry
            // if (counter) {
            //     for (let i = 0; i < counter; i++) {
            //         window.alert(`LINE 35\n${writableArray[i]} and i = ${i}`)
            //         let oldLift = writableArray[i]
                    
            //         if (oldLift.name === lift) {
            //             if (oldLift.max >= weight) {
            //                 window.alert(`${oldLift.name} ALREADY RECORDED AT ${oldLift.max}`)
            //                 return false;
            //             } else {
            //                 oldLift.max = weight;
            //                 counter++;
            //                 return true;
            //             }
            //         }
            //     }
            // }


    //         $writableArray = [...$writableArray, {
    //             name: lift,
    //             max: weight
    //         }];
    //         counter++;
    //     } else {
    //         window.alert("NUMBER NOT PASSED TO WEIGHT!\nTRY AGAIN!");
    //     }
    // };

3. Random notes I left:
    /*
    can't think straight due to being sick. doing this for now to check for whether or not
    the array has at least one entry. 

    when an entry exists, we iterate over the whole array to make sure that a lift has already
    been entered. if there is a match we check to make sure the new weight being entered is greater
    than the lift recorded. if the weight is less than or equal to, the user is warned that the 
    lift has already been entered into their log.

    /////////////////////////////////////////////////////////////

    keep in mind for the entry that white space is not accounted for, need to strip strings to reduce
    duplicated being entered.

    /////////////////////////////////////////////////////////////

    move new lift form to top of table
    */