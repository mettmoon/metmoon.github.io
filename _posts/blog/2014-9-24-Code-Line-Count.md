---
layout: post
title: 이번 프로젝트에서 작성 한 코드 라인 수
category: programming
tags: [ios,xcode]

---

최근에 진행된 아이폰 어플리케이션 개발 프로젝트에서 외부 라이브러리를 제외한 입력 소스 코드 라인 수 입니다.


```
385 ./Classes/HPServerManager.m
      72 ./Classes/HPServiceManager.m
      90 ./Classes/OSAppDataManager.m
     160 ./Classes/OSAppDataViewController.m
      13 ./Classes/RRAdItem.m
     185 ./Classes/RRAppDataManager.m
     930 ./Classes/RRDataManager.m
      18 ./Classes/RRDebugManager.m
      13 ./Classes/RROnAirInfo.m
      13 ./Classes/RRPhotoItem.m
      19 ./Classes/RRProgram.m
      18 ./Classes/RRRadioNetwork.m
      13 ./Classes/RRRelistenGroupItem.m
      18 ./Classes/RRSchedule.m
      13 ./Classes/RRSongDaumInfo.m
      21 ./Classes/RRSongItem.m
     151 ./GeneralFunction.m
      40 ./HPMenuNavigationController.m
     225 ./HPSideMenuViewController.m
      18 ./main.m
      12 ./OSAppDataItem.m
     192 ./OSShareManager.m
      34 ./OSSideMenuCell.m
      19 ./OSSideMenuSectionHeaderView.m
     154 ./OSTadManager.m
     308 ./RRAgreeViewController.m
      20 ./RRAppDataSwitchCell.m
     107 ./RRAppDelegate.m
     420 ./RRAudioPlayerController.m
     118 ./RRCBSLoginViewController.m
      34 ./RRDatePickerViewController.m
      54 ./RRDayPickerViewController.m
     392 ./RRDrawerController.m
      41 ./RRFlowAdViewController.m
      59 ./RRFullAdvertisementViewController.m
     113 ./RRHelperPageViewController.m
      88 ./RRHelperViewController.m
      46 ./RRImageViewController.m
     247 ./RRIntroViewController.m
     132 ./RRLocalStationListViewController.m
     144 ./RRLoginViewController.m
     363 ./RRMemberInfo2ViewController.m
     215 ./RRMemberInfoViewController.m
      80 ./RRNavigationController.m
      28 ./RRNetworkItemCell.m
      53 ./RRNoticeItem.m
      35 ./RRNoticeItemCell.m
     114 ./RRNoticeListViewController.m
     103 ./RRNoticeViewController.m
     378 ./RROnAirViewController.m
     308 ./RRPhotoDetailViewController.m
     198 ./RRPhotoListViewController.m
     129 ./RRPlayerView.m
      58 ./RRProgramFormCell.m
      25 ./RRProgramFormHeaderView.m
     315 ./RRProgramFormViewController.m
     261 ./RRProgramRootViewController.m
     303 ./RRProgramViewController.m
      42 ./RRRecordingItemCell.m
     210 ./RRRecordingListViewController.m
      24 ./RRRecordItem.m
      96 ./RRRelistenDetailCell.m
     382 ./RRRelistenDetailListViewController.m
      13 ./RRRelistenItem.m
      37 ./RRRelistenItemCell.m
     232 ./RRRelistenListViewController.m
      41 ./RRRelistenPlayerViewController.m
      75 ./RRRelistenTopCell.m
      24 ./RRSelectTitleView.m
     206 ./RRSignUpViewController.m
      79 ./RRSongCell.m
     353 ./RRSongListViewController.m
      67 ./RRTalkCell.m
      12 ./RRTalkItem.m
      13 ./RRTalkRoom.m
     452 ./RRTalkViewController.m
      51 ./RRTextField.m
      45 ./RRTextViewController.m
      91 ./RRUserInfoViewController.m
     278 ./RRUserSongListViewController.m
     114 ./RRVideoAdViewController.m
      41 ./RRVisitInfoCell.m
     142 ./RRVisitInfoViewController.m
      60 ./Settings/SettingsAppLinkCell.m
      34 ./Settings/SettingsDetailCell.m
      31 ./Settings/SettingsHeaderView.m
      35 ./Settings/SettingsLabelCell.m
      32 ./Settings/SettingsSegmentedCell.m
      43 ./Settings/SettingsSwitchCell.m
     941 ./Settings/SettingsViewController.m
      34 ./SettingsTimePickerCell.m
      19 ./UIImage+VersionUtility.m
     155 ./UIViewController+RRViewController.m
   12619 total
```
아래 커멘드를 소스코드폴더에서 실행 시키면 위 결과가 나옵니다.

```
find . "(" -name "*.m" -or -name "*.mm" -or -name "*.cpp" ")" -print0 | xargs -0 wc -l
```

코드 수가 개발자가 투입한 리소스를 100% 보여주는 건 아니지만 그냥 올려봤습니다.

저는 스토리보드와 nib을 최대한 활용하며 코드 재사용을 지향합니다.







P.S. 그래도 코드를 입력할 때가 가장 신명나지..