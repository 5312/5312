<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <title></title>
    <meta name="renderer" content="webkit">
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
    <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">
    <link rel="stylesheet" href="layuiadmin/layui/css/layui.css" media="all">
    <link rel="stylesheet" href="layuiadmin/style/admin.css" media="all">
    <link rel="stylesheet" href="src/all.css" media="all">
  <style>
  
  /*
  Malik Dellidj - @Dathink

  Solar System orbit animation true time scaled

  Revolution of planets in earth days (from Wikipedia)
  Mercury : ~87,5 days
  Venus : ~224,7 days
  Earth : ~365,2563 days
    + Moon : ~27,3216 days (around earth)
  Mars : ~687 days (~1,8 year)
  Jupiter : ~4 331 days (~12 years)
  Saturn : ~10 747 days (~30 years)
  Uranus : ~30 589 days (~84 years)
  Neptune : ~59 802 days (~165 years)
  Pluto : ~90 580 days (~248 years)
*/
*, *:before, *:after {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

html, body {
  height: 100%;
  width: 100%;
}

body {
  font: normal 1em/1.45em "Helvetica Neue", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  color: #fff;
  background: radial-gradient(ellipse at bottom, #1C2837 0%, #050608 100%);
  background-attachment: fixed;
}

h1 {
  font-weight: 300;
  font-size: 2.5em;
  text-transform: uppercase;
  font-family: Lato;
  line-height: 1.6em;
  letter-spacing: 0.1em;
}

a, a:visited {
  text-decoration: none;
  color: white;
  opacity: 0.7;
}
a:hover, a:visited:hover {
  opacity: 1;
}
a.icon, a:visited.icon {
  margin-right: 2px;
  padding: 3px;
}

.description {
  padding: 30px;
  position: absolute;
  top: 0;
  left: 0;
  width: 25%;
  z-index: 999;
}
.description p {
  font-size: 0.9em;
}
.description p + p {
  margin-top: 20px;
}
.description p.author {
  font-size: 0.7em;
}
.description p.author .fa-heart {
  color: #860014;
}

hr {
  margin: 26px 0;
  border: 0;
  border-top: 1px solid white;
  background: transparent;
  width: 25%;
  opacity: 0.1;
}

code {
  color: #ae94c0;
  font-family: Menlo, Monaco, Consolas, "Courier New", monospace;
  font-size: 0.9em;
}

.solar-syst {
  margin: 0 auto;
  width: 100%;
  height: 100%;
  position: relative;
}
.solar-syst:after {
  content: "";
  position: absolute;
  height: 2px;
  width: 2px;
  top: -2px;
  background: white;
  box-shadow: 583px 218px 0 0px rgba(255, 255, 255, 0.059) , 186px 1592px 0 0px rgba(255,255,255, 0.452) , 1127px 633px 0 0px rgba(255,255,255, 0.86) , 1343px 24px 0 0px rgba(255,255,255, 0.76) , 462px 1732px 0 0px rgba(255,255,255, 0.705) , 1460px 1006px 0 0px rgba(255,255,255, 0.241) , 1374px 1458px 0 0px rgba(255,255,255, 0.504) , 84px 874px 0 0px rgba(255,255,255, 0.166) , 334px 1641px 0 0px rgba(255,255,255, 0.863) , 475px 1734px 0 0px rgba(255,255,255, 0.499) , 1758px 1348px 0 0px rgba(255,255,255, 0.968) , 1798px 497px 0 0px rgba(255,255,255, 0.227) , 1151px 1272px 0 0px rgba(255,255,255, 0.063) , 142px 1691px 0 0px rgba(255,255,255, 0.938) , 1534px 728px 0 0px rgba(255,255,255, 0.843) , 1173px 583px 0 0px rgba(255,255,255, 0.145) , 450px 390px 0 0px rgba(255,255,255, 0.596) , 1766px 483px 0 0px rgba(255,255,255, 0.968) , 246px 1491px 0 0px rgba(255,255,255, 0.58) , 163px 396px 0 0px rgba(255,255,255, 0.988) , 1233px 685px 0 0px rgba(255,255,255, 0.885) , 379px 895px 0 0px rgba(255,255,255, 0.766) , 1510px 1388px 0 0px rgba(255,255,255, 0.091) , 756px 230px 0 0px rgba(255,255,255, 0.196) , 822px 325px 0 0px rgba(255,255,255, 0.771) , 185px 476px 0 0px rgba(255,255,255, 0.356) , 892px 723px 0 0px rgba(255,255,255, 0.65) , 962px 1403px 0 0px rgba(255,255,255, 0.184) , 855px 558px 0 0px rgba(255,255,255, 0.935) , 1330px 1263px 0 0px rgba(255,255,255, 0.878) , 758px 668px 0 0px rgba(255,255,255, 0.196) , 751px 873px 0 0px rgba(255,255,255, 0.272) , 556px 1251px 0 0px rgba(255,255,255, 0.01) , 120px 1202px 0 0px rgba(255,255,255, 0.314) , 745px 593px 0 0px rgba(255,255,255, 0.497) , 888px 515px 0 0px rgba(255,255,255, 0.545) , 506px 188px 0 0px rgba(255,255,255, 0.769) , 1536px 666px 0 0px rgba(255,255,255, 0.457) , 1377px 491px 0 0px rgba(255,255,255, 0.071) , 343px 1589px 0 0px rgba(255,255,255, 0.965) , 483px 599px 0 0px rgba(255,255,255, 0.651) , 656px 898px 0 0px rgba(255,255,255, 0.944) , 694px 521px 0 0px rgba(255,255,255, 0.92) , 1367px 538px 0 0px rgba(255,255,255, 0.34) , 1634px 251px 0 0px rgba(255,255,255, 0.076) , 1586px 285px 0 0px rgba(255,255,255, 0.264) , 727px 716px 0 0px rgba(255,255,255, 0.772) , 486px 1725px 0 0px rgba(255,255,255, 0.005) , 914px 1725px 0 0px rgba(255,255,255, 0.418) , 1535px 711px 0 0px rgba(255,255,255, 0.867) , 540px 1029px 0 0px rgba(255,255,255, 0.598) , 1519px 832px 0 0px rgba(255,255,255, 0.472) , 349px 636px 0 0px rgba(255,255,255, 0.855) , 1515px 1160px 0 0px rgba(255,255,255, 0.881) , 1197px 1018px 0 0px rgba(255,255,255, 0.332) , 1219px 158px 0 0px rgba(255,255,255, 0.736) , 98px 1268px 0 0px rgba(255,255,255, 0.126) , 1449px 676px 0 0px rgba(255,255,255, 0.255) , 1133px 1010px 0 0px rgba(255,255,255, 0.989) , 1252px 3px 0 0px rgba(255,255,255, 0.832) , 1452px 688px 0 0px rgba(255,255,255, 0.772) , 596px 339px 0 0px rgba(255,255,255, 0.919) , 974px 59px 0 0px rgba(255,255,255, 0.33) , 1461px 430px 0 0px rgba(255,255,255, 0.661) , 234px 201px 0 0px rgba(255,255,255, 0.008) , 131px 619px 0 0px rgba(255,255,255, 0.499) , 1524px 711px 0 0px rgba(255,255,255, 0.346) , 1656px 1103px 0 0px rgba(255,255,255, 0.956) , 914px 1784px 0 0px rgba(255,255,255, 0.75) , 401px 1204px 0 0px rgba(255,255,255, 0.387) , 825px 1373px 0 0px rgba(255,255,255, 0.798) , 1341px 1495px 0 0px rgba(255,255,255, 0.626) , 972px 91px 0 0px rgba(255,255,255, 0.013) , 989px 1011px 0 0px rgba(255,255,255, 0.778) , 14px 1597px 0 0px rgba(255,255,255, 0.642) , 339px 454px 0 0px rgba(255,255,255, 0.724) , 1562px 292px 0 0px rgba(255,255,255, 0.982) , 418px 573px 0 0px rgba(255,255,255, 0.862) , 1665px 1588px 0 0px rgba(255,255,255, 0.537) , 543px 1359px 0 0px rgba(255,255,255, 0.518) , 1202px 1418px 0 0px rgba(255,255,255, 0.056) , 1026px 1641px 0 0px rgba(255,255,255, 0.455) , 1096px 19px 0 0px rgba(255,255,255, 0.398) , 1291px 1511px 0 0px rgba(255,255,255, 0.568) , 1643px 216px 0 0px rgba(255,255,255, 0.944) , 249px 1444px 0 0px rgba(255,255,255, 0.473) , 863px 1442px 0 0px rgba(255,255,255, 0.296) , 186px 1368px 0 0px rgba(255,255,255, 0.811) , 1662px 1545px 0 0px rgba(255,255,255, 0.936) , 1180px 710px 0 0px rgba(255,255,255, 0.578) , 1589px 28px 0 0px rgba(255,255,255, 0.229) , 334px 554px 0 0px rgba(255,255,255, 0.109) , 1059px 1566px 0 0px rgba(255,255,255, 0.397) , 913px 921px 0 0px rgba(255,255,255, 0.302) , 388px 546px 0 0px rgba(255,255,255, 0.801) , 1620px 374px 0 0px rgba(255,255,255, 0.107) , 912px 899px 0 0px rgba(255,255,255, 0.526) , 568px 8px 0 0px rgba(255,255,255, 0.408) , 1420px 112px 0 0px rgba(255,255,255, 0.909) , 539px 1516px 0 0px rgba(255,255,255, 0.169) , 8px 881px 0 0px rgba(255,255,255, 0.07) , 1489px 1318px 0 0px rgba(255,255,255, 0.687) , 1176px 29px 0 0px rgba(255,255,255, 0.426) , 1319px 246px 0 0px rgba(255,255,255, 0.144) , 341px 415px 0 0px rgba(255,255,255, 0.023) , 1250px 753px 0 0px rgba(255,255,255, 0.732) , 1035px 317px 0 0px rgba(255,255,255, 0.108) , 1478px 233px 0 0px rgba(255,255,255, 0.138) , 132px 645px 0 0px rgba(255,255,255, 0.24) , 1151px 934px 0 0px rgba(255,255,255, 0.964) , 1653px 86px 0 0px rgba(255,255,255, 0.945) , 841px 1266px 0 0px rgba(255,255,255, 0.531) , 1791px 1280px 0 0px rgba(255,255,255, 0.246) , 134px 57px 0 0px rgba(255,255,255, 0.04) , 1557px 1620px 0 0px rgba(255,255,255, 0.321) , 139px 581px 0 0px rgba(255,255,255, 0.826) , 1162px 1726px 0 0px rgba(255,255,255, 0.873) , 407px 1358px 0 0px rgba(255,255,255, 0.586) , 153px 322px 0 0px rgba(255,255,255, 0.825) , 374px 280px 0 0px rgba(255,255,255, 0.46) , 1429px 1788px 0 0px rgba(255,255,255, 0.51) , 822px 557px 0 0px rgba(255,255,255, 0.729) , 19px 1797px 0 0px rgba(255,255,255, 0.28) , 654px 55px 0 0px rgba(255,255,255, 0.293) , 1457px 31px 0 0px rgba(255,255,255, 0.649) , 946px 1428px 0 0px rgba(255,255,255, 0.385) , 564px 670px 0 0px rgba(255,255,255, 0.018) , 1414px 1649px 0 0px rgba(255,255,255, 0.717) , 846px 1324px 0 0px rgba(255,255,255, 0.984) , 710px 1px 0 0px rgba(255,255,255, 0.656) , 1694px 1153px 0 0px rgba(255,255,255, 0.009) , 496px 5px 0 0px rgba(255,255,255, 0.808) , 1119px 1196px 0 0px rgba(255,255,255, 0.376) , 137px 1112px 0 0px rgba(255,255,255, 0.173) , 1664px 1007px 0 0px rgba(255,255,255, 0.98) , 460px 653px 0 0px rgba(255,255,255, 0.149) , 1382px 23px 0 0px rgba(255,255,255, 0.176) , 1514px 1533px 0 0px rgba(255,255,255, 0.517) , 919px 1505px 0 0px rgba(255,255,255, 0.062) , 149px 150px 0 0px rgba(255,255,255, 0.417) , 1552px 687px 0 0px rgba(255,255,255, 0.312) , 95px 249px 0 0px rgba(255,255,255, 0.663) , 1275px 446px 0 0px rgba(255,255,255, 0.503) , 1431px 716px 0 0px rgba(255,255,255, 0.413) , 343px 1043px 0 0px rgba(255,255,255, 0.36) , 1047px 1098px 0 0px rgba(255,255,255, 0.356) , 973px 579px 0 0px rgba(255,255,255, 0.646) , 166px 697px 0 0px rgba(255,255,255, 0.368) , 1056px 84px 0 0px rgba(255,255,255, 0.641) , 1028px 1264px 0 0px rgba(255,255,255, 0.737) , 563px 833px 0 0px rgba(255,255,255, 0.747) , 921px 28px 0 0px rgba(255,255,255, 0.969) , 1502px 1556px 0 0px rgba(255,255,255, 0.098) , 290px 18px 0 0px rgba(255,255,255, 0.83) , 119px 1783px 0 0px rgba(255,255,255, 0.985) , 1356px 344px 0 0px rgba(255,255,255, 0.713) , 542px 1028px 0 0px rgba(255,255,255, 0.115) , 855px 1265px 0 0px rgba(255,255,255, 0.388) , 1206px 915px 0 0px rgba(255,255,255, 0.236) , 1354px 1615px 0 0px rgba(255,255,255, 0.808) , 1286px 673px 0 0px rgba(255,255,255, 0.048) , 696px 1360px 0 0px rgba(255,255,255, 0.931) , 1055px 1122px 0 0px rgba(255,255,255, 0.17) , 937px 1285px 0 0px rgba(255,255,255, 0.341) , 940px 770px 0 0px rgba(255,255,255, 0.798) , 941px 956px 0 0px rgba(255,255,255, 0.261) , 921px 802px 0 0px rgba(255,255,255, 0.312) , 345px 154px 0 0px rgba(255,255,255, 0.521) , 1031px 1614px 0 0px rgba(255,255,255, 0.044) , 1471px 1363px 0 0px rgba(255,255,255, 0.885) , 971px 807px 0 0px rgba(255,255,255, 0.272) , 417px 491px 0 0px rgba(255,255,255, 0.608) , 16px 1071px 0 0px rgba(255,255,255, 0.964) , 684px 356px 0 0px rgba(255,255,255, 0.882) , 1013px 1470px 0 0px rgba(255,255,255, 0.61) , 1389px 1580px 0 0px rgba(255,255,255, 0.68) , 811px 865px 0 0px rgba(255,255,255, 0.788) , 711px 1283px 0 0px rgba(255,255,255, 0.702) , 739px 1482px 0 0px rgba(255,255,255, 0.774) , 330px 899px 0 0px rgba(255,255,255, 0.486) , 236px 864px 0 0px rgba(255,255,255, 0.141) , 393px 1575px 0 0px rgba(255,255,255, 0.692) , 934px 1078px 0 0px rgba(255,255,255, 0.778) , 1433px 1186px 0 0px rgba(255,255,255, 0.802) , 1724px 1593px 0 0px rgba(255,255,255, 0.374) , 723px 1181px 0 0px rgba(255,255,255, 0.257) , 916px 1323px 0 0px rgba(255,255,255, 0.145) , 103px 1035px 0 0px rgba(255,255,255, 0.442) , 1586px 782px 0 0px rgba(255,255,255, 0.109) , 1008px 519px 0 0px rgba(255,255,255, 0.125) , 474px 199px 0 0px rgba(255,255,255, 0.997) , 1272px 314px 0 0px rgba(255,255,255, 0.862) , 758px 524px 0 0px rgba(255,255,255, 0.883) , 1354px 756px 0 0px rgba(255,255,255, 0.486) , 1532px 732px 0 0px rgba(255,255,255, 0.748) , 1466px 1030px 0 0px rgba(255,255,255, 0.174) , 981px 90px 0 0px rgba(255,255,255, 0.795) , 192px 196px 0 0px rgba(255,255,255, 0.945) , 1585px 710px 0 0px rgba(255,255,255, 0.491) , 941px 283px 0 0px rgba(255,255,255, 0.783) , 742px 1471px 0 0px rgba(255,255,255, 0.294) , 1146px 74px 0 0px rgba(255,255,255, 0.81) , 710px 462px 0 0px rgba(255,255,255, 0.229) , 220px 1128px 0 0px rgba(255,255,255, 0.913) , 479px 1263px 0 0px rgba(255,255,255, 0.687) , 1036px 1011px 0 0px rgba(255,255,255, 0.788) , 330px 917px 0 0px rgba(255,255,255, 0.749) , 268px 593px 0 0px rgba(255,255,255, 0.173) , 73px 691px 0 0px rgba(255,255,255, 0.764) , 159px 352px 0 0px rgba(255,255,255, 0.796) , 776px 358px 0 0px rgba(255,255,255, 0.136) , 1615px 147px 0 0px rgba(255,255,255, 0.121) , 324px 985px 0 0px rgba(255,255,255, 0.581) , 953px 1674px 0 0px rgba(255,255,255, 0.658) , 635px 1013px 0 0px rgba(255,255,255, 0.604) , 724px 590px 0 0px rgba(255,255,255, 0.673) , 500px 1751px 0 0px rgba(255,255,255, 0.469) , 468px 1512px 0 0px rgba(255,255,255, 0.885) , 990px 889px 0 0px rgba(255,255,255, 0.243) , 1548px 601px 0 0px rgba(255,255,255, 0.453) , 204px 1633px 0 0px rgba(255,255,255, 0.348) , 632px 819px 0 0px rgba(255,255,255, 0.651) , 1246px 1291px 0 0px rgba(255,255,255, 0.665) , 885px 870px 0 0px rgba(255,255,255, 0.813) , 77px 1513px 0 0px rgba(255,255,255, 0.316) , 655px 1537px 0 0px rgba(255,255,255, 0.705) , 514px 153px 0 0px rgba(255,255,255, 0.236) , 1297px 1586px 0 0px rgba(255,255,255, 0.446) , 1475px 1170px 0 0px rgba(255,255,255, 0.969) , 240px 1580px 0 0px rgba(255,255,255, 0.978) , 1026px 1153px 0 0px rgba(255,255,255, 0.559) , 1471px 1382px 0 0px rgba(255,255,255, 0.548) , 1215px 1228px 0 0px rgba(255,255,255, 0.343) , 29px 75px 0 0px rgba(255,255,255, 0.17) , 1552px 1108px 0 0px rgba(255,255,255, 0.131) , 676px 716px 0 0px rgba(255,255,255, 0.234) , 1694px 32px 0 0px rgba(255,255,255, 0.309) , 842px 759px 0 0px rgba(255,255,255, 0.578) , 383px 1061px 0 0px rgba(255,255,255, 0.452) , 1131px 791px 0 0px rgba(255,255,255, 0.323) , 51px 1617px 0 0px rgba(255,255,255, 0.733) , 1039px 1179px 0 0px rgba(255,255,255, 0.504) , 1103px 855px 0 0px rgba(255,255,255, 0.388) , 608px 1680px 0 0px rgba(255,255,255, 0.234) , 37px 1038px 0 0px rgba(255,255,255, 0.855) , 1146px 1142px 0 0px rgba(255,255,255, 0.011) , 58px 460px 0 0px rgba(255,255,255, 0.687) , 880px 615px 0 0px rgba(255,255,255, 0.218) , 272px 1118px 0 0px rgba(255,255,255, 0.418) , 1377px 1068px 0 0px rgba(255,255,255, 0.852) , 712px 1453px 0 0px rgba(255,255,255, 0.512) , 1182px 1779px 0 0px rgba(255,255,255, 0.071) , 1354px 885px 0 0px rgba(255,255,255, 0.269) , 1070px 591px 0 0px rgba(255,255,255, 0.764) , 503px 671px 0 0px rgba(255,255,255, 0.308) , 928px 873px 0 0px rgba(255,255,255, 0.221) , 874px 1304px 0 0px rgba(255,255,255, 0.069) , 352px 1640px 0 0px rgba(255,255,255, 0.743) , 875px 1447px 0 0px rgba(255,255,255, 0.234) , 1602px 1161px 0 0px rgba(255,255,255, 0.627) , 1427px 963px 0 0px rgba(255,255,255, 0.267) , 122px 517px 0 0px rgba(255,255,255, 0.372) , 1360px 199px 0 0px rgba(255,255,255, 0.94) , 810px 1594px 0 0px rgba(255,255,255, 0.27) , 653px 389px 0 0px rgba(255,255,255, 0.197) , 37px 778px 0 0px rgba(255,255,255, 0.199) , 907px 1542px 0 0px rgba(255,255,255, 0.503) , 1042px 311px 0 0px rgba(255,255,255, 0.098) , 1548px 781px 0 0px rgba(255,255,255, 0.333) , 1368px 435px 0 0px rgba(255,255,255, 0.928) , 1308px 439px 0 0px rgba(255,255,255, 0.176) , 1578px 474px 0 0px rgba(255,255,255, 0.251) , 844px 891px 0 0px rgba(255,255,255, 0.779) , 1428px 1575px 0 0px rgba(255,255,255, 0.207) , 610px 712px 0 0px rgba(255,255,255, 0.744) , 272px 1093px 0 0px rgba(255,255,255, 0.773) , 429px 1455px 0 0px rgba(255,255,255, 0.514) , 892px 1742px 0 0px rgba(255,255,255, 0.019) , 1736px 1402px 0 0px rgba(255,255,255, 0.941) , 278px 1699px 0 0px rgba(255,255,255, 0.717) , 78px 1575px 0 0px rgba(255,255,255, 0.423) , 1241px 1225px 0 0px rgba(255,255,255, 0.526) , 899px 559px 0 0px rgba(255,255,255, 0.594) , 1432px 120px 0 0px rgba(255,255,255, 0.615) , 266px 1579px 0 0px rgba(255,255,255, 0.773) , 1654px 656px 0 0px rgba(255,255,255, 0.937) , 313px 170px 0 0px rgba(255,255,255, 0.479) , 1540px 1621px 0 0px rgba(255,255,255, 0.577) , 1349px 802px 0 0px rgba(255,255,255, 0.731) , 880px 864px 0 0px rgba(255,255,255, 0.182) , 1173px 50px 0 0px rgba(255,255,255, 0.985) , 135px 447px 0 0px rgba(255,255,255, 0.757) , 109px 871px 0 0px rgba(255,255,255, 0.589) , 1426px 1217px 0 0px rgba(255,255,255, 0.736) , 790px 1288px 0 0px rgba(255,255,255, 0.483) , 1699px 726px 0 0px rgba(255,255,255, 1) , 84px 361px 0 0px rgba(255,255,255, 0.966) , 282px 524px 0 0px rgba(255,255,255, 0.956) , 1079px 789px 0 0px rgba(255,255,255, 0.65) , 652px 247px 0 0px rgba(255,255,255, 0.316) , 895px 621px 0 0px rgba(255,255,255, 0.596) , 1552px 815px 0 0px rgba(255,255,255, 0.428) , 215px 407px 0 0px rgba(255,255,255, 0.343) , 832px 511px 0 0px rgba(255,255,255, 0.285) , 1040px 305px 0 0px rgba(255,255,255, 0.792) , 920px 909px 0 0px rgba(255,255,255, 0.096) , 1061px 570px 0 0px rgba(255,255,255, 0.017) , 1119px 1063px 0 0px rgba(255,255,255, 0.127) , 1522px 631px 0 0px rgba(255,255,255, 0.027) , 1234px 86px 0 0px rgba(255,255,255, 0.088) , 1437px 316px 0 0px rgba(255,255,255, 0.097) , 456px 1101px 0 0px rgba(255,255,255, 0.413) , 546px 633px 0 0px rgba(255,255,255, 0.781) , 536px 557px 0 0px rgba(255,255,255, 0.685) , 1633px 672px 0 0px rgba(255,255,255, 0.505) , 1791px 782px 0 0px rgba(255,255,255, 0.514) , 1224px 841px 0 0px rgba(255,255,255, 0.989) , 477px 1346px 0 0px rgba(255,255,255, 0.066) , 775px 340px 0 0px rgba(255,255,255, 0.816) , 1425px 529px 0 0px rgba(255,255,255, 0.14) , 575px 387px 0 0px rgba(255,255,255, 0.383) , 799px 372px 0 0px rgba(255,255,255, 0.689) , 1176px 771px 0 0px rgba(255,255,255, 0.552) , 1385px 505px 0 0px rgba(255,255,255, 0.509) , 961px 920px 0 0px rgba(255,255,255, 0.109) , 1662px 933px 0 0px rgba(255,255,255, 0.659) , 962px 740px 0 0px rgba(255,255,255, 0.559) , 232px 1354px 0 0px rgba(255,255,255, 0.66) , 1302px 1395px 0 0px rgba(255,255,255, 0.744) , 1145px 1696px 0 0px rgba(255,255,255, 0.876) , 426px 1205px 0 0px rgba(255,255,255, 0.15) , 1311px 1276px 0 0px rgba(255,255,255, 0.362) , 1198px 23px 0 0px rgba(255,255,255, 0.313) , 1339px 1486px 0 0px rgba(255,255,255, 0.104) , 1479px 1408px 0 0px rgba(255,255,255, 0.417) , 650px 889px 0 0px rgba(255,255,255, 0.294) , 1295px 1615px 0 0px rgba(255,255,255, 0.421) , 1419px 103px 0 0px rgba(255,255,255, 0.189) , 915px 1026px 0 0px rgba(255,255,255, 0.366) , 531px 707px 0 0px rgba(255,255,255, 0.812) , 1417px 896px 0 0px rgba(255,255,255, 0.015) , 982px 1160px 0 0px rgba(255,255,255, 0.084) , 1597px 380px 0 0px rgba(255,255,255, 0.173) , 226px 1088px 0 0px rgba(255,255,255, 0.82) , 1191px 844px 0 0px rgba(255,255,255, 0.137) , 1317px 1612px 0 0px rgba(255,255,255, 0.348) , 193px 353px 0 0px rgba(255,255,255, 0.913) , 1511px 525px 0 0px rgba(255,255,255, 0.146) , 727px 476px 0 0px rgba(255,255,255, 0.206) , 984px 1754px 0 0px rgba(255,255,255, 0.129) , 1316px 493px 0 0px rgba(255,255,255, 0.235) , 1457px 494px 0 0px rgba(255,255,255, 0.096) , 1207px 69px 0 0px rgba(255,255,255, 0.078) , 1393px 679px 0 0px rgba(255,255,255, 0.617) , 425px 1046px 0 0px rgba(255,255,255, 0.014) , 748px 510px 0 0px rgba(255,255,255, 0.33) , 848px 1467px 0 0px rgba(255,255,255, 0.711) , 1281px 1792px 0 0px rgba(255,255,255, 0.901) , 1744px 1193px 0 0px rgba(255,255,255, 0.343) , 1226px 440px 0 0px rgba(255,255,255, 0.624) , 540px 634px 0 0px rgba(255,255,255, 0.621) , 795px 866px 0 0px rgba(255,255,255, 0.258) , 1218px 1306px 0 0px rgba(255,255,255, 0.793) , 1567px 616px 0 0px rgba(255,255,255, 0.522) , 1510px 94px 0 0px rgba(255,255,255, 0.208) , 1409px 803px 0 0px rgba(255,255,255, 0.082) , 1655px 1619px 0 0px rgba(255,255,255, 0.868) , 254px 1460px 0 0px rgba(255,255,255, 0.286) , 1503px 402px 0 0px rgba(255,255,255, 0.65) , 1579px 494px 0 0px rgba(255,255,255, 0.18) , 53px 581px 0 0px rgba(255,255,255, 0.082) , 1305px 1740px 0 0px rgba(255,255,255, 0.568) , 976px 1553px 0 0px rgba(255,255,255, 0.772) , 132px 453px 0 0px rgba(255,255,255, 0.156) , 1504px 1631px 0 0px rgba(255,255,255, 0.4) , 1758px 677px 0 0px rgba(255,255,255, 0.78) , 858px 21px 0 0px rgba(255,255,255, 0.325) , 1228px 871px 0 0px rgba(255,255,255, 0.754) , 1020px 324px 0 0px rgba(255,255,255, 0.876) , 901px 1035px 0 0px rgba(255,255,255, 0.64) , 1281px 562px 0 0px rgba(255,255,255, 0.125) , 1071px 1403px 0 0px rgba(255,255,255, 0.621) , 526px 1733px 0 0px rgba(255,255,255, 0.602) , 1260px 867px 0 0px rgba(255,255,255, 0.988) , 646px 819px 0 0px rgba(255,255,255, 0.503) , 1235px 96px 0 0px rgba(255,255,255, 0.301) , 57px 1521px 0 0px rgba(255,255,255, 0.672) , 257px 1478px 0 0px rgba(255,255,255, 0.207) , 25px 177px 0 0px rgba(255,255,255, 0.236) , 1076px 1376px 0 0px rgba(255,255,255, 0.989) , 1145px 796px 0 0px rgba(255,255,255, 0.955) , 118px 1259px 0 0px rgba(255,255,255, 0.856) , 639px 153px 0 0px rgba(255,255,255, 0.546) , 1232px 1675px 0 0px rgba(255,255,255, 0.675) , 607px 194px 0 0px rgba(255,255,255, 0.439) , 610px 1639px 0 0px rgba(255,255,255, 0.649) , 136px 1320px 0 0px rgba(255,255,255, 0.784) , 1122px 1075px 0 0px rgba(255,255,255, 0.368) , 1525px 212px 0 0px rgba(255,255,255, 0.824) , 1030px 1005px 0 0px rgba(255,255,255, 0.781) , 60px 1023px 0 0px rgba(255,255,255, 0.802) , 1415px 46px 0 0px rgba(255,255,255, 0.765) , 296px 1069px 0 0px rgba(255,255,255, 0.798) , 1101px 977px 0 0px rgba(255,255,255, 0.112) , 1152px 1766px 0 0px rgba(255,255,255, 0.947) , 281px 756px 0 0px rgba(255,255,255, 0.507) , 1132px 933px 0 0px rgba(255,255,255, 0.492) , 328px 1566px 0 0px rgba(255,255,255, 0.048) , 704px 1154px 0 0px rgba(255,255,255, 0.813) , 1280px 1435px 0 0px rgba(255,255,255, 0.523) , 613px 262px 0 0px rgba(255,255,255, 0.89) , 1062px 1351px 0 0px rgba(255,255,255, 0.544) , 204px 1610px 0 0px rgba(255,255,255, 0.857) , 701px 1200px 0 0px rgba(255,255,255, 0.229) , 1547px 1550px 0 0px rgba(255,255,255, 0.723) , 635px 1253px 0 0px rgba(255,255,255, 0.726) , 743px 477px 0 0px rgba(255,255,255, 0.969) , 1014px 317px 0 0px rgba(255,255,255, 0.309) , 282px 277px 0 0px rgba(255,255,255, 0.782) , 1455px 1470px 0 0px rgba(255,255,255, 0.728) , 756px 1334px 0 0px rgba(255,255,255, 0.661) , 1062px 659px 0 0px rgba(255,255,255, 0.888) , 440px 1205px 0 0px rgba(255,255,255, 0.245) , 267px 114px 0 0px rgba(255,255,255, 0.928) , 429px 656px 0 0px rgba(255,255,255, 0.196) , 1187px 94px 0 0px rgba(255,255,255, 0.129) , 253px 1418px 0 0px rgba(255,255,255, 0.078) , 809px 996px 0 0px rgba(255,255,255, 0.581) , 1327px 1218px 0 0px rgba(255,255,255, 0.387) , 1643px 510px 0 0px rgba(255,255,255, 0.745) , 1589px 1508px 0 0px rgba(255,255,255, 0.003) , 704px 1295px 0 0px rgba(255,255,255, 0.456) , 653px 14px 0 0px rgba(255,255,255, 0.457) , 775px 30px 0 0px rgba(255,255,255, 0.851) , 803px 1505px 0 0px rgba(255,255,255, 0.256) , 506px 1384px 0 0px rgba(255,255,255, 0.492) , 533px 376px 0 0px rgba(255,255,255, 0.495) , 1783px 509px 0 0px rgba(255,255,255, 0.416) , 563px 435px 0 0px rgba(255,255,255, 0.158) , 1293px 951px 0 0px rgba(255,255,255, 0.762) , 68px 1383px 0 0px rgba(255,255,255, 0.716) , 829px 528px 0 0px rgba(255,255,255, 0.405) , 113px 1329px 0 0px rgba(255,255,255, 0.622) , 1414px 219px 0 0px rgba(255,255,255, 0.458) , 288px 416px 0 0px rgba(255,255,255, 0.783) , 1407px 1757px 0 0px rgba(255,255,255, 0.644) , 1752px 851px 0 0px rgba(255,255,255, 0.509) , 1578px 1450px 0 0px rgba(255,255,255, 0.489) , 541px 724px 0 0px rgba(255,255,255, 0.195) , 1681px 842px 0 0px rgba(255,255,255, 0.776) , 105px 1581px 0 0px rgba(255,255,255, 0.555) , 1430px 866px 0 0px rgba(255,255,255, 0.383) , 750px 221px 0 0px rgba(255,255,255, 0.145) , 842px 105px 0 0px rgba(255,255,255, 0.607) , 594px 262px 0 0px rgba(255,255,255, 0.926) , 614px 746px 0 0px rgba(255,255,255, 0.819) , 1728px 704px 0 0px rgba(255,255,255, 0.299) , 1139px 1027px 0 0px rgba(255,255,255, 0.588) , 525px 1155px 0 0px rgba(255,255,255, 0.562) , 867px 109px 0 0px rgba(255,255,255, 0.738) , 341px 745px 0 0px rgba(255,255,255, 0.206) , 1250px 1655px 0 0px rgba(255,255,255, 0.766) , 363px 683px 0 0px rgba(255,255,255, 0.936) , 86px 1160px 0 0px rgba(255,255,255, 0.214) , 993px 262px 0 0px rgba(255,255,255, 0.115) , 53px 336px 0 0px rgba(255,255,255, 0.427) , 1349px 119px 0 0px rgba(255,255,255, 0.433) , 805px 99px 0 0px rgba(255,255,255, 0.555) , 1729px 438px 0 0px rgba(255,255,255, 0.603) , 1109px 973px 0 0px rgba(255,255,255, 0.436) , 330px 1184px 0 0px rgba(255,255,255, 0.967) , 23px 471px 0 0px rgba(255,255,255, 0.284) , 1525px 1707px 0 0px rgba(255,255,255, 0.574) , 774px 785px 0 0px rgba(255,255,255, 0.58) , 1115px 965px 0 0px rgba(255,255,255, 0.466) , 1226px 378px 0 0px rgba(255,255,255, 0.642) , 120px 1622px 0 0px rgba(255,255,255, 0.568) , 508px 1326px 0 0px rgba(255,255,255, 0.987) , 1426px 1714px 0 0px rgba(255,255,255, 0.494) , 1287px 1726px 0 0px rgba(255,255,255, 0.597) , 404px 527px 0 0px rgba(255,255,255, 0.37) , 315px 127px 0 0px rgba(255,255,255, 0.615) , 1352px 1143px 0 0px rgba(255,255,255, 0.933) , 492px 758px 0 0px rgba(255,255,255, 0.113) , 1250px 222px 0 0px rgba(255,255,255, 0.825) , 365px 1700px 0 0px rgba(255,255,255, 0.811) , 664px 481px 0 0px rgba(255,255,255, 0.074) , 1267px 684px 0 0px rgba(255,255,255, 0.078) , 604px 472px 0 0px rgba(255,255,255, 0.302) , 936px 1501px 0 0px rgba(255,255,255, 0.773) , 928px 1099px 0 0px rgba(255,255,255, 0.175) , 215px 338px 0 0px rgba(255,255,255, 0.561) , 1401px 1778px 0 0px rgba(255,255,255, 0.832) , 1031px 85px 0 0px rgba(255,255,255, 0.03) , 1352px 139px 0 0px rgba(255,255,255, 0.354) , 291px 825px 0 0px rgba(255,255,255, 0.92) , 334px 607px 0 0px rgba(255,255,255, 0.894) , 885px 391px 0 0px rgba(255,255,255, 0.618) , 66px 895px 0 0px rgba(255,255,255, 0.609) , 664px 591px 0 0px rgba(255,255,255, 0.364);
  border-radius: 100px;
}
.solar-syst div {
  border-radius: 1000px;
  top: 50%;
  left: 50%;
  position: absolute;
  z-index: 999;
}
.solar-syst div:not(.sun) {
  border: 1px solid rgba(102, 166, 229, 0.12);
}
.solar-syst div:not(.sun):before {
  left: 50%;
  border-radius: 100px;
  content: "";
  position: absolute;
}
.solar-syst div:not(.asteroids-belt):before {
  box-shadow: inset 0 6px 0 -2px rgba(0, 0, 0, 0.25);
}

.sun {
  background: radial-gradient(ellipse at center, #ffd000 1%, #f9b700 39%, #f9b700 39%, #e06317 100%);
  height: 40px;
  width: 40px;
  margin-top: -20px;
  margin-left: -20px;
  background-clip: padding-box;
  border: 0 !important;
  background-position: -28px -103px;
  background-size: 175%;
  box-shadow: 0 0 10px 2px rgba(255, 107, 0, 0.4), 0 0 22px 11px rgba(255, 203, 0, 0.13);
}

.mercury {
  height: 70px;
  width: 70px;
  margin-top: -35px;
  margin-left: -35px;
  -webkit-animation: orb 7.1867343561s linear infinite;
          animation: orb 7.1867343561s linear infinite;
}
.mercury:before {
  height: 4px;
  width: 4px;
  background: #9f5e26;
  margin-top: -2px;
  margin-left: -2px;
}

.venus {
  height: 100px;
  width: 100px;
  margin-top: -50px;
  margin-left: -50px;
  -webkit-animation: orb 18.4555338265s linear infinite;
          animation: orb 18.4555338265s linear infinite;
}
.venus:before {
  height: 8px;
  width: 8px;
  background: #BEB768;
  margin-top: -4px;
  margin-left: -4px;
}

.earth {
  height: 145px;
  width: 145px;
  margin-top: -72.5px;
  margin-left: -72.5px;
  -webkit-animation: orb 30s linear infinite;
          animation: orb 30s linear infinite;
}
.earth:before {
  height: 6px;
  width: 6px;
  background: #11abe9;
  margin-top: -3px;
  margin-left: -3px;
}
.earth:after {
  position: absolute;
  content: "";
  height: 18px;
  width: 18px;
  left: 50%;
  top: 0px;
  margin-left: -9px;
  margin-top: -9px;
  border-radius: 100px;
  box-shadow: 0 -10px 0 -8px grey;
  -webkit-animation: orb 2.2440352158s linear infinite;
          animation: orb 2.2440352158s linear infinite;
}

.mars {
  height: 190px;
  width: 190px;
  margin-top: -95px;
  margin-left: -95px;
  -webkit-animation: orb 56.4261314589s linear infinite;
          animation: orb 56.4261314589s linear infinite;
}
.mars:before {
  height: 6px;
  width: 6px;
  background: #cf3921;
  margin-top: -3px;
  margin-left: -3px;
}

.jupiter {
  height: 340px;
  width: 340px;
  margin-top: -170px;
  margin-left: -170px;
  -webkit-animation: orb 355.7228171013s linear infinite;
          animation: orb 355.7228171013s linear infinite;
}
.jupiter:before {
  height: 18px;
  width: 18px;
  background: #c76e2a;
  margin-top: -9px;
  margin-left: -9px;
}

.saturn {
  height: 440px;
  width: 440px;
  margin-top: -220px;
  margin-left: -220px;
  -webkit-animation: orb 882.6952471456s linear infinite;
          animation: orb 882.6952471456s linear infinite;
}
.saturn:before {
  height: 12px;
  width: 12px;
  background: #e7c194;
  margin-top: -6px;
  margin-left: -6px;
}
.saturn:after {
  position: absolute;
  content: "";
  height: 2.34%;
  width: 4.676%;
  left: 50%;
  top: 0px;
  transform: rotateZ(-52deg);
  margin-left: -2.3%;
  margin-top: -1.2%;
  border-radius: 50% 50% 50% 50%;
  box-shadow: 0 1px 0 1px #987641, 3px 1px 0 #987641, -3px 1px 0 #987641;
  -webkit-animation: orb 882.6952471456s linear infinite;
          animation: orb 882.6952471456s linear infinite;
  animation-direction: reverse;
  transform-origin: 52% 60%;
}

.uranus {
  height: 520px;
  width: 520px;
  margin-top: -260px;
  margin-left: -260px;
  -webkit-animation: orb 2512.4001967933s linear infinite;
          animation: orb 2512.4001967933s linear infinite;
}
.uranus:before {
  height: 10px;
  width: 10px;
  background: #b5e3e3;
  margin-top: -5px;
  margin-left: -5px;
}

.neptune {
  height: 630px;
  width: 630px;
  margin-top: -315px;
  margin-left: -315px;
  -webkit-animation: orb 4911.7838624549s linear infinite;
          animation: orb 4911.7838624549s linear infinite;
}
.neptune:before {
  height: 10px;
  width: 10px;
  background: #175e9e;
  margin-top: -5px;
  margin-left: -5px;
}

.asteroids-belt {
  opacity: 0.7;
  border-color: transparent !important;
  height: 300px;
  width: 300px;
  margin-top: -150px;
  margin-left: -150px;
  -webkit-animation: orb 179.9558282773s linear infinite;
          animation: orb 179.9558282773s linear infinite;
  overflow: hidden;
}
.asteroids-belt:before {
  top: 50%;
  height: 210px;
  width: 210px;
  margin-left: -105px;
  margin-top: -105px;
  background: transparent;
  border-radius: 140px !important;
  box-shadow: -5px -82px 0 -104px rgba(255, 255, 255, 0.827) , -64px -135px 0 -104px rgba(255,255,255, 0.588) , 7px -43px 0 -104px rgba(255,255,255, 0.225) , 101px -103px 0 -104px rgba(255,255,255, 0.582) , 98px 123px 0 -104px rgba(255,255,255, 0.373) , -54px -104px 0 -104px rgba(255,255,255, 0.649) , 105px 75px 0 -104px rgba(255,255,255, 0.848) , -18px -4px 0 -104px rgba(255,255,255, 0.026) , -77px -44px 0 -104px rgba(255,255,255, 0.484) , -120px -2px 0 -104px rgba(255,255,255, 0.218) , -138px 82px 0 -104px rgba(255,255,255, 0.57) , -93px -31px 0 -104px rgba(255,255,255, 0.367) , 111px -13px 0 -104px rgba(255,255,255, 0.371) , -106px -51px 0 -104px rgba(255,255,255, 0.351) , -93px 76px 0 -104px rgba(255,255,255, 0.602) , -99px -60px 0 -104px rgba(255,255,255, 0.896) , -109px 80px 0 -104px rgba(255,255,255, 0.763) , 3px -100px 0 -104px rgba(255,255,255, 0.601) , 5px 71px 0 -104px rgba(255,255,255, 0.518) , 14px -85px 0 -104px rgba(255,255,255, 0.733) , -76px 75px 0 -104px rgba(255,255,255, 0.088) , 67px -60px 0 -104px rgba(255,255,255, 0.52) , 30px -133px 0 -104px rgba(255,255,255, 0.338) , -86px -40px 0 -104px rgba(255,255,255, 0.134) , 43px 120px 0 -104px rgba(255,255,255, 0.594) , -108px -48px 0 -104px rgba(255,255,255, 0.331) , -90px 70px 0 -104px rgba(255,255,255, 0.937) , 79px 44px 0 -104px rgba(255,255,255, 0.49) , 11px 24px 0 -104px rgba(255,255,255, 0.9) , 5px -93px 0 -104px rgba(255,255,255, 0.82) , -91px -23px 0 -104px rgba(255,255,255, 0.768) , 35px 127px 0 -104px rgba(255,255,255, 0.752) , 50px 51px 0 -104px rgba(255,255,255, 0.169) , -60px -137px 0 -104px rgba(255,255,255, 0.34) , -12px -38px 0 -104px rgba(255,255,255, 0.962) , 44px 96px 0 -104px rgba(255,255,255, 0.86) , -32px -65px 0 -104px rgba(255,255,255, 0.663) , -78px -34px 0 -104px rgba(255,255,255, 0.589) , 48px 109px 0 -104px rgba(255,255,255, 0.064) , -139px -26px 0 -104px rgba(255,255,255, 0.825) , -42px 107px 0 -104px rgba(255,255,255, 0.321) , 53px -27px 0 -104px rgba(255,255,255, 0.263) , -43px 109px 0 -104px rgba(255,255,255, 0.151) , -31px 29px 0 -104px rgba(255,255,255, 0.155) , -58px 131px 0 -104px rgba(255,255,255, 0.151) , 103px -122px 0 -104px rgba(255,255,255, 0.051) , -49px -19px 0 -104px rgba(255,255,255, 0.836) , 30px -29px 0 -104px rgba(255,255,255, 0.887) , 49px -112px 0 -104px rgba(255,255,255, 0.716) , -68px 22px 0 -104px rgba(255,255,255, 0.585) , 99px -11px 0 -104px rgba(255,255,255, 0.507) , -109px 36px 0 -104px rgba(255,255,255, 0.524) , -70px 125px 0 -104px rgba(255,255,255, 0.983) , 98px 82px 0 -104px rgba(255,255,255, 0.001) , -128px 112px 0 -104px rgba(255,255,255, 0.257) , 12px -55px 0 -104px rgba(255,255,255, 0.289) , -61px -91px 0 -104px rgba(255,255,255, 0.712) , -76px -76px 0 -104px rgba(255,255,255, 0.147) , 8px 66px 0 -104px rgba(255,255,255, 0.572) , 122px 43px 0 -104px rgba(255,255,255, 0.673) , -80px -94px 0 -104px rgba(255,255,255, 0.117) , -56px -19px 0 -104px rgba(255,255,255, 0.18) , 70px -123px 0 -104px rgba(255,255,255, 0.03) , 84px -12px 0 -104px rgba(255,255,255, 0.664) , -61px 46px 0 -104px rgba(255,255,255, 0.82) , 0px 98px 0 -104px rgba(255,255,255, 0.324) , 95px -30px 0 -104px rgba(255,255,255, 0.574) , 49px 109px 0 -104px rgba(255,255,255, 0.229) , 143px 50px 0 -104px rgba(255,255,255, 0.464) , 5px -18px 0 -104px rgba(255,255,255, 0.608) , -124px -96px 0 -104px rgba(255,255,255, 0.835) , -66px 129px 0 -104px rgba(255,255,255, 0.041) , 4px -123px 0 -104px rgba(255,255,255, 0.94) , -118px -83px 0 -104px rgba(255,255,255, 0.982) , 119px 19px 0 -104px rgba(255,255,255, 0.28) , -54px -59px 0 -104px rgba(255,255,255, 0.084) , -19px -112px 0 -104px rgba(255,255,255, 0.316) , 132px 8px 0 -104px rgba(255,255,255, 0.122) , 72px 93px 0 -104px rgba(255,255,255, 0.441) , 54px 70px 0 -104px rgba(255,255,255, 0.65) , -44px 16px 0 -104px rgba(255,255,255, 0.297) , 13px 91px 0 -104px rgba(255,255,255, 0.005) , -58px 74px 0 -104px rgba(255,255,255, 0.245) , 91px -61px 0 -104px rgba(255,255,255, 0.014) , -73px -31px 0 -104px rgba(255,255,255, 0.939) , -86px 86px 0 -104px rgba(255,255,255, 0.247) , -15px 43px 0 -104px rgba(255,255,255, 0.872) , -90px 36px 0 -104px rgba(255,255,255, 0.971) , -54px -129px 0 -104px rgba(255,255,255, 0.113) , -65px 38px 0 -104px rgba(255,255,255, 0.884) , 106px -8px 0 -104px rgba(255,255,255, 0.532) , 95px -61px 0 -104px rgba(255,255,255, 0.356) , -110px -54px 0 -104px rgba(255,255,255, 0.963) , -110px -64px 0 -104px rgba(255,255,255, 0.908) , 10px -107px 0 -104px rgba(255,255,255, 0.017) , 26px -126px 0 -104px rgba(255,255,255, 0.968) , 37px -94px 0 -104px rgba(255,255,255, 0.689) , -8px -77px 0 -104px rgba(255,255,255, 0.559) , -122px -49px 0 -104px rgba(255,255,255, 0.336) , -5px -129px 0 -104px rgba(255,255,255, 0.351) , 6px 70px 0 -104px rgba(255,255,255, 0.093) , 88px 122px 0 -104px rgba(255,255,255, 0.437) , 16px -63px 0 -104px rgba(255,255,255, 0.565) , -104px -39px 0 -104px rgba(255,255,255, 0.145) , 40px 144px 0 -104px rgba(255,255,255, 0.4) , -112px 89px 0 -104px rgba(255,255,255, 0.972) , 109px 124px 0 -104px rgba(255,255,255, 0.697) , 39px 15px 0 -104px rgba(255,255,255, 0.462) , 48px -45px 0 -104px rgba(255,255,255, 0.623) , -34px -53px 0 -104px rgba(255,255,255, 0.861) , -21px 49px 0 -104px rgba(255,255,255, 0.533) , 23px 45px 0 -104px rgba(255,255,255, 0.272) , -84px 113px 0 -104px rgba(255,255,255, 0.32) , 8px 115px 0 -104px rgba(255,255,255, 0.892) , 92px 94px 0 -104px rgba(255,255,255, 0.115) , 2px 111px 0 -104px rgba(255,255,255, 0.306) , -15px 23px 0 -104px rgba(255,255,255, 0.192) , -30px 5px 0 -104px rgba(255,255,255, 0.644) , -78px 101px 0 -104px rgba(255,255,255, 0.268) , -45px 14px 0 -104px rgba(255,255,255, 0.828) , -92px 105px 0 -104px rgba(255,255,255, 0.943) , 1px -23px 0 -104px rgba(255,255,255, 0.547) , -10px -25px 0 -104px rgba(255,255,255, 0.438) , -114px -104px 0 -104px rgba(255,255,255, 0.266) , 78px -127px 0 -104px rgba(255,255,255, 0.605) , -29px 19px 0 -104px rgba(255,255,255, 0.971) , 19px 3px 0 -104px rgba(255,255,255, 0.709) , 136px -5px 0 -104px rgba(255,255,255, 0.596) , 115px 86px 0 -104px rgba(255,255,255, 0.358) , -100px -31px 0 -104px rgba(255,255,255, 0.939) , 19px 115px 0 -104px rgba(255,255,255, 0.038) , 74px 145px 0 -104px rgba(255,255,255, 0.655) , 66px 134px 0 -104px rgba(255,255,255, 0.941) , -6px -131px 0 -104px rgba(255,255,255, 0.631) , -99px -20px 0 -104px rgba(255,255,255, 0.002) , 17px -77px 0 -104px rgba(255,255,255, 0.706) , 83px -140px 0 -104px rgba(255,255,255, 0.748) , 112px -100px 0 -104px rgba(255,255,255, 0.132) , -89px -128px 0 -104px rgba(255,255,255, 0.829) , -34px 35px 0 -104px rgba(255,255,255, 0.713) , -11px -101px 0 -104px rgba(255,255,255, 0.917) , 101px 110px 0 -104px rgba(255,255,255, 0.763) , -49px 57px 0 -104px rgba(255,255,255, 0.472) , -26px -1px 0 -104px rgba(255,255,255, 0.871) , -44px -85px 0 -104px rgba(255,255,255, 0.656) , -85px -59px 0 -104px rgba(255,255,255, 0.539) , 12px 77px 0 -104px rgba(255,255,255, 0.313) , -6px 73px 0 -104px rgba(255,255,255, 0.21) , 37px -102px 0 -104px rgba(255,255,255, 0.663) , 29px 137px 0 -104px rgba(255,255,255, 0.986) , 36px 69px 0 -104px rgba(255,255,255, 0.469) , -33px -57px 0 -104px rgba(255,255,255, 0.152) , -24px -24px 0 -104px rgba(255,255,255, 0.095) , 131px 112px 0 -104px rgba(255,255,255, 0.949) , -52px -8px 0 -104px rgba(255,255,255, 0.602) , 72px -5px 0 -104px rgba(255,255,255, 0.88) , -2px 137px 0 -104px rgba(255,255,255, 0.141) , 2px -50px 0 -104px rgba(255,255,255, 0.558) , 110px -137px 0 -104px rgba(255,255,255, 0.685) , -108px 135px 0 -104px rgba(255,255,255, 0.095) , 33px 78px 0 -104px rgba(255,255,255, 0.136) , -73px 38px 0 -104px rgba(255,255,255, 0.669) , 79px -85px 0 -104px rgba(255,255,255, 0.128) , -14px -53px 0 -104px rgba(255,255,255, 0.784) , -68px -44px 0 -104px rgba(255,255,255, 0.323) , -120px 97px 0 -104px rgba(255,255,255, 0.101) , 125px 9px 0 -104px rgba(255,255,255, 0.449) , -57px -87px 0 -104px rgba(255,255,255, 0.749) , 127px 84px 0 -104px rgba(255,255,255, 0.547) , -39px -69px 0 -104px rgba(255,255,255, 0.431) , 128px 118px 0 -104px rgba(255,255,255, 0.288) , -60px 18px 0 -104px rgba(255,255,255, 0.15) , 22px 99px 0 -104px rgba(255,255,255, 0.023) , 62px -61px 0 -104px rgba(255,255,255, 0.64) , 96px 123px 0 -104px rgba(255,255,255, 0.509) , -94px -35px 0 -104px rgba(255,255,255, 0.686) , 140px -119px 0 -104px rgba(255,255,255, 0.459) , 73px -143px 0 -104px rgba(255,255,255, 0.564) , 70px -53px 0 -104px rgba(255,255,255, 0.88) , 39px -68px 0 -104px rgba(255,255,255, 0.331) , -139px 118px 0 -104px rgba(255,255,255, 0.182) , 71px -84px 0 -104px rgba(255,255,255, 0.673) , 22px -124px 0 -104px rgba(255,255,255, 0.832) , -54px 131px 0 -104px rgba(255,255,255, 0.705) , 77px -11px 0 -104px rgba(255,255,255, 0.055) , 124px -99px 0 -104px rgba(255,255,255, 0.694) , 122px -88px 0 -104px rgba(255,255,255, 0.202) , 48px 9px 0 -104px rgba(255,255,255, 0.153) , -76px 12px 0 -104px rgba(255,255,255, 0.266) , -70px 132px 0 -104px rgba(255,255,255, 0.309) , -93px 80px 0 -104px rgba(255,255,255, 0.524) , 126px 82px 0 -104px rgba(255,255,255, 0.497) , 97px 11px 0 -104px rgba(255,255,255, 0.101) , -61px -28px 0 -104px rgba(255,255,255, 0.498) , -117px 123px 0 -104px rgba(255,255,255, 0.566) , 68px -6px 0 -104px rgba(255,255,255, 0.363) , -85px -127px 0 -104px rgba(255,255,255, 0.12) , -73px 145px 0 -104px rgba(255,255,255, 0.172) , 119px 107px 0 -104px rgba(255,255,255, 0.902) , 102px 8px 0 -104px rgba(255,255,255, 0.923) , 137px -73px 0 -104px rgba(255,255,255, 0.815) , 23px -80px 0 -104px rgba(255,255,255, 0.352) , -32px -137px 0 -104px rgba(255,255,255, 0.265) , 63px 120px 0 -104px rgba(255,255,255, 0.277) , -63px -57px 0 -104px rgba(255,255,255, 0.045) , -57px -142px 0 -104px rgba(255,255,255, 0.083) , 120px 64px 0 -104px rgba(255,255,255, 0.128) , 76px -133px 0 -104px rgba(255,255,255, 0.965) , -28px 61px 0 -104px rgba(255,255,255, 0.266) , -75px -50px 0 -104px rgba(255,255,255, 0.574) , 137px 40px 0 -104px rgba(255,255,255, 0.643) , -142px -79px 0 -104px rgba(255,255,255, 0.555) , 52px -136px 0 -104px rgba(255,255,255, 0.896) , -80px 64px 0 -104px rgba(255,255,255, 0.106) , 30px 111px 0 -104px rgba(255,255,255, 0.748) , -30px -74px 0 -104px rgba(255,255,255, 0.348) , 45px 108px 0 -104px rgba(255,255,255, 0.102) , 15px 113px 0 -104px rgba(255,255,255, 0.543) , -104px -59px 0 -104px rgba(255,255,255, 0.252) , -140px 9px 0 -104px rgba(255,255,255, 0.752) , -109px -27px 0 -104px rgba(255,255,255, 0.6) , -24px -24px 0 -104px rgba(255,255,255, 0.042) , 55px -68px 0 -104px rgba(255,255,255, 0.846) , 127px 44px 0 -104px rgba(255,255,255, 0.4) , -109px -87px 0 -104px rgba(255,255,255, 0.417) , 7px -26px 0 -104px rgba(255,255,255, 0.475) , -119px -18px 0 -104px rgba(255,255,255, 0.101) , -10px -42px 0 -104px rgba(255,255,255, 0.384) , 126px 65px 0 -104px rgba(255,255,255, 0.43) , 134px -62px 0 -104px rgba(255,255,255, 0.996) , 18px -11px 0 -104px rgba(255,255,255, 0.067) , 92px 28px 0 -104px rgba(255,255,255, 0.203) , 133px -137px 0 -104px rgba(255,255,255, 0.168) , -88px -9px 0 -104px rgba(255,255,255, 0.596) , -16px -73px 0 -104px rgba(255,255,255, 0.275) , 111px -35px 0 -104px rgba(255,255,255, 0.069) , 45px 63px 0 -104px rgba(255,255,255, 0.629) , -1px -18px 0 -104px rgba(255,255,255, 0.824) , -48px 133px 0 -104px rgba(255,255,255, 0.477) , -130px -64px 0 -104px rgba(255,255,255, 0.89) , -68px -23px 0 -104px rgba(255,255,255, 0.803) , 130px 108px 0 -104px rgba(255,255,255, 0.994) , -24px -70px 0 -104px rgba(255,255,255, 0.562) , 98px 145px 0 -104px rgba(255,255,255, 0.969) , 48px 55px 0 -104px rgba(255,255,255, 0.428) , -73px 14px 0 -104px rgba(255,255,255, 0.997) , -84px -77px 0 -104px rgba(255,255,255, 0.662) , 38px -141px 0 -104px rgba(255,255,255, 0.213) , 59px -101px 0 -104px rgba(255,255,255, 0.563) , 129px -88px 0 -104px rgba(255,255,255, 0.611) , -59px 23px 0 -104px rgba(255,255,255, 0.673) , -98px 144px 0 -104px rgba(255,255,255, 0.78) , -62px -25px 0 -104px rgba(255,255,255, 0.952) , 9px -101px 0 -104px rgba(255,255,255, 0.775) , -7px 114px 0 -104px rgba(255,255,255, 0.01) , 78px 55px 0 -104px rgba(255,255,255, 0.82) , 46px 58px 0 -104px rgba(255,255,255, 0.993) , 51px 18px 0 -104px rgba(255,255,255, 0.308) , 132px 17px 0 -104px rgba(255,255,255, 0.964) , 54px -109px 0 -104px rgba(255,255,255, 0.778) , -97px -96px 0 -104px rgba(255,255,255, 0.921) , 141px -79px 0 -104px rgba(255,255,255, 0.387) , 22px -70px 0 -104px rgba(255,255,255, 0.209) , -119px -84px 0 -104px rgba(255,255,255, 0.496) , 85px -107px 0 -104px rgba(255,255,255, 0.398) , 54px 52px 0 -104px rgba(255,255,255, 0.085) , -96px 91px 0 -104px rgba(255,255,255, 0.56) , -19px 67px 0 -104px rgba(255,255,255, 0.665) , -32px 130px 0 -104px rgba(255,255,255, 0.522) , 20px -97px 0 -104px rgba(255,255,255, 0.313) , 127px -103px 0 -104px rgba(255,255,255, 0.039) , 5px -66px 0 -104px rgba(255,255,255, 0.536) , -66px -144px 0 -104px rgba(255,255,255, 0.712) , 3px 28px 0 -104px rgba(255,255,255, 0.452) , -128px 40px 0 -104px rgba(255,255,255, 0.965) , -10px 114px 0 -104px rgba(255,255,255, 0.567) , 56px 119px 0 -104px rgba(255,255,255, 0.331) , -135px 89px 0 -104px rgba(255,255,255, 0.077) , -49px 78px 0 -104px rgba(255,255,255, 0.107) , 5px 107px 0 -104px rgba(255,255,255, 0.257) , 130px -32px 0 -104px rgba(255,255,255, 0.148) , -2px -36px 0 -104px rgba(255,255,255, 0.152) , 75px 57px 0 -104px rgba(255,255,255, 0.16) , 7px -76px 0 -104px rgba(255,255,255, 0.678) , 36px -44px 0 -104px rgba(255,255,255, 0.601) , -3px -117px 0 -104px rgba(255,255,255, 0.099) , 56px -33px 0 -104px rgba(255,255,255, 0.467) , -127px -21px 0 -104px rgba(255,255,255, 0.815) , -42px 22px 0 -104px rgba(255,255,255, 0.535) , -113px 121px 0 -104px rgba(255,255,255, 0.735) , -114px -51px 0 -104px rgba(255,255,255, 0.525) , -140px 70px 0 -104px rgba(255,255,255, 0.849) , 25px 52px 0 -104px rgba(255,255,255, 0.102) , -139px 97px 0 -104px rgba(255,255,255, 0.486) , -130px 34px 0 -104px rgba(255,255,255, 0.915) , 144px 115px 0 -104px rgba(255,255,255, 0.337) , -109px -99px 0 -104px rgba(255,255,255, 0.153) , -118px 39px 0 -104px rgba(255,255,255, 0.336) , 60px 82px 0 -104px rgba(255,255,255, 0.706) , 96px -55px 0 -104px rgba(255,255,255, 0.467) , -28px 76px 0 -104px rgba(255,255,255, 0.711) , 106px 76px 0 -104px rgba(255,255,255, 0.34) , -136px -14px 0 -104px rgba(255,255,255, 0.665) , 53px 78px 0 -104px rgba(255,255,255, 0.851) , -80px -44px 0 -104px rgba(255,255,255, 0.807) , -79px 119px 0 -104px rgba(255,255,255, 0.392) , -60px 13px 0 -104px rgba(255,255,255, 0.865) , 63px 139px 0 -104px rgba(255,255,255, 0.579) , 115px -131px 0 -104px rgba(255,255,255, 0.442) , 141px -8px 0 -104px rgba(255,255,255, 0.906) , -28px 18px 0 -104px rgba(255,255,255, 0.806) , 1px -104px 0 -104px rgba(255,255,255, 0.666) , 57px 45px 0 -104px rgba(255,255,255, 0.882) , 42px -83px 0 -104px rgba(255,255,255, 0.425) , -13px -79px 0 -104px rgba(255,255,255, 0.614) , -93px 136px 0 -104px rgba(255,255,255, 0.59) , 25px -114px 0 -104px rgba(255,255,255, 0.937) , -24px -106px 0 -104px rgba(255,255,255, 0.487) , 111px 6px 0 -104px rgba(255,255,255, 0.147) , -28px -13px 0 -104px rgba(255,255,255, 0.575) , 60px 92px 0 -104px rgba(255,255,255, 0.794) , -130px -80px 0 -104px rgba(255,255,255, 0.841) , 111px 90px 0 -104px rgba(255,255,255, 0.689) , -134px -65px 0 -104px rgba(255,255,255, 0.806) , -51px -52px 0 -104px rgba(255,255,255, 0.764) , 121px -115px 0 -104px rgba(255,255,255, 0.024) , 6px -108px 0 -104px rgba(255,255,255, 0.8) , 135px -120px 0 -104px rgba(255,255,255, 0.062) , 122px -98px 0 -104px rgba(255,255,255, 0.146) , 57px 62px 0 -104px rgba(255,255,255, 0.598) , 50px 88px 0 -104px rgba(255,255,255, 0.784) , -70px 125px 0 -104px rgba(255,255,255, 0.399) , 133px 127px 0 -104px rgba(255,255,255, 0.653) , -1px 8px 0 -104px rgba(255,255,255, 0.729) , -142px 60px 0 -104px rgba(255,255,255, 0.083) , 21px -103px 0 -104px rgba(255,255,255, 0.102) , -31px -46px 0 -104px rgba(255,255,255, 0.648) , -110px -17px 0 -104px rgba(255,255,255, 0.869) , -21px 21px 0 -104px rgba(255,255,255, 0.433) , 118px 48px 0 -104px rgba(255,255,255, 0.254) , -125px -15px 0 -104px rgba(255,255,255, 0.495) , 89px 39px 0 -104px rgba(255,255,255, 0.044) , -67px 128px 0 -104px rgba(255,255,255, 0.086) , 129px 135px 0 -104px rgba(255,255,255, 0.345) , -22px -62px 0 -104px rgba(255,255,255, 0.212) , -124px -34px 0 -104px rgba(255,255,255, 0.816) , 54px 125px 0 -104px rgba(255,255,255, 0.923) , -88px -18px 0 -104px rgba(255,255,255, 0.667) , -23px -61px 0 -104px rgba(255,255,255, 0.564) , -47px 128px 0 -104px rgba(255,255,255, 0.871) , -68px 49px 0 -104px rgba(255,255,255, 0.347) , -125px -90px 0 -104px rgba(255,255,255, 0.9) , -4px 55px 0 -104px rgba(255,255,255, 0.193) , 129px -74px 0 -104px rgba(255,255,255, 0.439) , 119px 33px 0 -104px rgba(255,255,255, 0.964) , -89px 25px 0 -104px rgba(255,255,255, 0.475) , 132px 20px 0 -104px rgba(255,255,255, 0.753) , -34px 102px 0 -104px rgba(255,255,255, 0.235) , -126px -60px 0 -104px rgba(255,255,255, 0.643) , 64px 67px 0 -104px rgba(255,255,255, 0.698) , 54px 108px 0 -104px rgba(255,255,255, 0.105) , 59px -129px 0 -104px rgba(255,255,255, 0.68) , -103px 94px 0 -104px rgba(255,255,255, 0.378) , 90px 31px 0 -104px rgba(255,255,255, 0.025) , -116px 56px 0 -104px rgba(255,255,255, 0.557) , -52px 105px 0 -104px rgba(255,255,255, 0.333) , 121px 110px 0 -104px rgba(255,255,255, 0.397) , -92px 33px 0 -104px rgba(255,255,255, 0.019) , 125px -113px 0 -104px rgba(255,255,255, 0.665) , -29px -2px 0 -104px rgba(255,255,255, 0.803) , 55px -4px 0 -104px rgba(255,255,255, 0.734) , 86px 21px 0 -104px rgba(255,255,255, 0.316) , -20px 122px 0 -104px rgba(255,255,255, 0.908) , -66px -124px 0 -104px rgba(255,255,255, 0.318) , 90px -93px 0 -104px rgba(255,255,255, 0.782) , -75px 115px 0 -104px rgba(255,255,255, 0.132) , 12px -49px 0 -104px rgba(255,255,255, 0.346) , 17px -90px 0 -104px rgba(255,255,255, 0.88) , 39px -91px 0 -104px rgba(255,255,255, 0.895) , -127px -16px 0 -104px rgba(255,255,255, 0.207) , -129px -112px 0 -104px rgba(255,255,255, 0.226) , 95px 60px 0 -104px rgba(255,255,255, 0.144) , 8px 134px 0 -104px rgba(255,255,255, 0.32) , 84px -74px 0 -104px rgba(255,255,255, 0.582) , -41px -10px 0 -104px rgba(255,255,255, 0.552) , 80px 135px 0 -104px rgba(255,255,255, 0.8) , -44px 13px 0 -104px rgba(255,255,255, 0.632) , 67px -105px 0 -104px rgba(255,255,255, 0.862) , 15px 1px 0 -104px rgba(255,255,255, 0.881) , -77px -53px 0 -104px rgba(255,255,255, 0.054);
}

.pluto {
  height: 780px;
  width: 780px;
  margin-top: -450px;
  margin-left: -320px;
  -webkit-animation: orb 7439.7074054575s linear infinite;
          animation: orb 7439.7074054575s linear infinite;
}
.pluto:before {
  height: 3px;
  width: 3px;
  background: #fff;
  margin-top: -1.5px;
  margin-left: -1.5px;
}

.hide {
  display: none;
}

.links {
  margin-top: 5px !important;
  font-size: 1em !important;
}

@-webkit-keyframes orb {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(-360deg);
  }
}

@keyframes orb {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(-360deg);
  }
}
  </style>
 </head> 
<div class='solar-syst'>
  <div class='sun'></div>
  <div class='mercury'></div>
  <div class='venus'></div>
  <div class='earth'></div>
  <div class='mars'></div>
  <div class='jupiter'></div>
  <div class='saturn'></div>
  <div class='uranus'></div>
  <div class='neptune'></div>
  <div class='pluto'></div>
  <div class='asteroids-belt'></div>
</div>
  </html>
