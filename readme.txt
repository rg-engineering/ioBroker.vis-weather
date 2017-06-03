var dp_cloud = "Clouds";

                            var dp = "hour";
                            var values_cloud = [];
                            var maxY_cloud = 100;
                            var minY_cloud = 0;
                            var cnt = 0;

                            //get date
                            var dateoid = data.instance + ".NextDaysDetailed.0d.date";
                            var sDate = vis.states[dateoid + '.val'];
                            //console.log("date was " + sDate);
                            var day = parseInt(sDate.substring(6, 8));
                            var month = parseInt(sDate.substring(4, 6));
                            var year = parseInt(sDate.substring(0, 4));

                            //test only
                            day = 12;

                            console.log("start with " + day + "." + month + "." + year)

                            
                            var lastHour = -1;
                            for (var d = 0; d < 5; d++) {

                                for (var p = 0; p < 8; p++) {
                                    //get rain values

                                    //get cloud values
                                    var oid_cloud = data.instance + ".NextDaysDetailed." + d + "d." + p + "h." + dp_cloud;
                                    var val = parseInt(vis.states[oid_cloud + '.val']);
                                    var val_cloud = 0;
                                    if (data.sunorcloud == "sun") { //invert value 
                                        val_cloud = 100 - val;
                                    }
                                    else {
                                        val_cloud = val;
                                    }


                                    // get time
                                    var oid = data.instance + ".NextDaysDetailed." + d + "d." + p + "h." + dp;
                                    var sTime = vis.states[oid + '.val'];

                                    var hours = parseInt(sTime.substring(0, 2));
                                    var minutes = parseInt(sTime.substring(3, 5));

                                    
                                    var oDate = new Date(year, month, day, hours, minutes, 0, 0);

                                    //check next day
                                    if (hours < lastHour) {
                                        oDate.setDate(oDate.getDate() + 1);
                                        day = oDate.getUTCDate();
                                        month = oDate.getUTCMonth();
                                        year = oDate.getUTCFullYear();
                                    }
                                    lastHour = hours;
                                    console.log(oid_cloud + " : " + val_cloud + "% " + oDate.getHours() + ":" + oDate.getMinutes() + " " + day + "." + month + "." + year);

                                    //need time in UTC                            
                                    var date = oDate.getTime();
                                    console.log(date);
                                    values_cloud.push([date, val_cloud]);
                                    cnt++;
                                }
                            }

                            //maxY += 0.1 * maxY;
                            //minY -= 0.1 * minY;

                            var barwidth = $div.width() / (cnt) - (parseFloat(data.barSpacing) || 1);
                            console.log("barwidth = " + barwidth);

                            var nXAxis = data.cloudswithxaxix ? 2 : 1;
                            console.log("xaxis = " + nXAxis);

                            var values_cloud_test = [];
                            var oDate_Test = new Date();
                            for (var i = 0; i < 15; i++)
                            {
                                console.log(oDate_Test.getTime()+ i)
                                values_cloud_test.push([oDate_Test.getTime(), i]);
                                oDate_Test.setDate(oDate_Test.getDate() + 1);
                            }


                            result=$.plot($div,
                                
                                {
                                    data: values_cloud_test,
                                    yaxis: 2,
                                    lines: { show: data.cloudschartType == "line" ? true : false, fill: false },
                                    bars: { show: data.cloudschartType == "bar" ? true : false }
                                } ,
                                {
                                    series: {
                                        lines: {},
                                        points: {},
                                        bars:
                                            {
                                                barWidth: barwidth
                                            }
                                    },
                                    xaxis:
                                      {
                                          mode: "time",
                                          tickLength: 5
                                      },
                                    yaxis:
                                      [{
                                          max: maxY_cloud,
                                          min: minY_cloud,
                                          alignTicksWithAxis: 1,
                                          position: 'left' //warum geht das nicht??? ist immer rechts...
                                      },
                                      {
                                          max: maxY_cloud,
                                          min: minY_cloud,
                                          alignTicksWithAxis: 1,
                                          position: 'right'
                                      }],
                                    grid:
                                      {
                                          //Farben einstellen fehlt noch
                                          backgroundColor: { colors: ["#fff", "#eee"] },
                                          borderWidth: {
                                              top: 1,
                                              right: 1,
                                              bottom: 2,
                                              left: 2
                                          },
                                          //fehlt noch
                                          //markings: nextDay
                                      }
                                }
                                );
                            console.log("result " + result.getOptions());