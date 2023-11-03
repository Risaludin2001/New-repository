/**
* GCP - dataflow job jjs for [用户信息 - user_info]
* AUTHOR BEJSON
*
* User-defined function (UDF) to transform events as part of a Dataflow template job.
* upload to GCS and create dataflow job with this js file and method as 'process'
* @param {string} inJson input Pub/Sub JSON message (stringified)
* @return {string} outJson output JSON message (stringified)
*/
function process(inJson) {
    //for local js debug
    //var obj = JSON.parse(JSON.stringify(inJson));
    //for online jjs
    var obj = JSON.parse(inJson);
    var includePubsubMessage = obj.data && obj.attributes;
    var data = includePubsubMessage ? obj.data : obj;
    //debug and show error if you need special logic
    if(data.hasOwnProperty('show_error')){
        throw new ERROR("show_error:"+JSON.stringify(data))
    }
    // INSERT CUSTOM TRANSFORMATION LOGIC HERE
    var tableObj= {};
    tableObj.insert_time=new Date().toUTCString()
    tableObj.user_id=data.userId
    tableObj.user_name=data.userName
    tableObj.status=data.status
    tableObj.create_time=data.createTime
    return JSON.stringify(tableObj);
}

//field name = field name
    tableObj.userId=data.userId
    tableObj.userName=data.userName
    tableObj.status=data.status
    tableObj.createTime=data.createTime

//column name = column name
    tableObj.user_id=data.user_id
    tableObj.user_name=data.user_name
    tableObj.status=data.status
    tableObj.create_time=data.create_time# New-repository
New repository
