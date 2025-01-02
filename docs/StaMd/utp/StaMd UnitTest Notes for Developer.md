---
layout: default
title: StaMd UnitTest Notes for Developer
nav_order: 7
parent: State and Modes
---
{% raw %}
<u>StaMd UnitTest Notes for Developer</u>

(Note: Below is for short term plans. Long term plan is to make TEST_CFG
folder more generic for projects)

To complete StaMd Unittest, StaMd files in GenData
folder(Ap_StaMd_Cfg.c, Ap_StaMd_Proxy.c) should also be unit tested.
These files are different across projects. Below steps should be
followed to send files to ODC

1.  Place files from GenData (Ap_StaMd_Cfg.c, Ap_StaMd_Proxy.c) in
    TEST_CFG folder of integration project .(For eg:
    BMW_UKL_MCV_EPS_TMS570\Tessy\Reports\StaMd).

2.  While submitting StaMd component to ODC for unittest, place TEST_CFG
    folder from step 1 in utp/contract folder of StaMd
    component(StaMd\utp\contract)

3.  And reports of StaMd component should be placed in integration
    project.(For eg: BMW_UKL_MCV_EPS_TMS570\Tessy\Reports\StaMd)

{% endraw %}