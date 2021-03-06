---
title: CKeyFrame 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboard
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAfterTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAtOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetExistingKeyframe
- AFXANIMATIONCONTROLLER/CKeyFrame::GetOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::m_offset
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pExistingKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pTransition
dev_langs:
- C++
helpviewer_keywords:
- CKeyFrame [MFC], CKeyFrame
- CKeyFrame [MFC], AddToStoryboard
- CKeyFrame [MFC], AddToStoryboardAfterTransition
- CKeyFrame [MFC], AddToStoryboardAtOffset
- CKeyFrame [MFC], GetExistingKeyframe
- CKeyFrame [MFC], GetOffset
- CKeyFrame [MFC], GetTransition
- CKeyFrame [MFC], m_offset
- CKeyFrame [MFC], m_pExistingKeyFrame
- CKeyFrame [MFC], m_pTransition
ms.assetid: d050a562-20f6-4c65-8ce5-ccb3aef1a20e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b5bdba80f0be5e6e47043b67934a79ea5039b4ed
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394234"
---
# <a name="ckeyframe-class"></a>CKeyFrame 类

表示动画关键帧。

## <a name="syntax"></a>语法

```
class CKeyFrame : public CBaseKeyFrame;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CKeyFrame::CKeyFrame](#ckeyframe)|已重载。 构造取决于其他关键帧的关键帧。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CKeyFrame::AddToStoryboard](#addtostoryboard)|将关键帧添加到情节提要。 (重写[CBaseKeyFrame::AddToStoryboard](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard)。)|
|[CKeyFrame::AddToStoryboardAfterTransition](#addtostoryboardaftertransition)|添加关键帧转换后的情节提要。|
|[CKeyFrame::AddToStoryboardAtOffset](#addtostoryboardatoffset)|添加关键帧偏移量位置处的情节提要。|
|[CKeyFrame::GetExistingKeyframe](#getexistingkeyframe)|返回指向此关键帧依赖的关键帧的指针。|
|[CKeyFrame::GetOffset](#getoffset)|返回从其他关键帧的偏移量。|
|[CKeyFrame::GetTransition](#gettransition)|返回一个指向此关键帧所依赖的转换。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CKeyFrame::m_offset](#m_offset)|指定从关键帧 m_pExistingKeyFrame 中存储此关键帧的偏移量。|
|[CKeyFrame::m_pExistingKeyFrame](#m_pexistingkeyframe)|存储指向现有关键帧的指针的指针。 此关键帧添加到与现有的关键帧的 m_offset 情节提要。|
|[CKeyFrame::m_pTransition](#m_ptransition)|存储指向过渡的关键帧开始。|

## <a name="remarks"></a>备注

此类实现动画关键帧。 关键帧表示情节提要中的某个时刻，并可用于指定转换的开始和结束时间。 关键帧可能基于其他关键帧和具有一个偏移量 （以秒为单位），或可能根据转换并且表示某个时间点这一转换的结束的时间。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)

[CKeyFrame](../../mfc/reference/ckeyframe-class.md)

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="addtostoryboard"></a>  CKeyFrame::AddToStoryboard

将关键帧添加到情节提要。

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>参数

*pStoryboard*<br/>
指向情节提要的指针。

*bDeepAdd*<br/>
指定是否添加关键帧或转换以递归方式。

### <a name="return-value"></a>返回值

为 TRUE，如果关键帧已成功添加。

### <a name="remarks"></a>备注

此方法将添加到情节提要的关键帧。 如果它依赖于其他关键帧或转换和 bDeepAdd 为 TRUE，此方法会尝试以递归方式添加它们。

##  <a name="addtostoryboardaftertransition"></a>  CKeyFrame::AddToStoryboardAfterTransition

添加关键帧转换后的情节提要。

```
BOOL AddToStoryboardAfterTransition(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>参数

*pStoryboard*<br/>
指向情节提要的指针。

*bDeepAdd*<br/>
指定是否转换以递归方式添加。

### <a name="return-value"></a>返回值

为 TRUE，如果关键帧已成功添加。

### <a name="remarks"></a>备注

要添加关键帧转换后的情节提要的框架调用此函数。

##  <a name="addtostoryboardatoffset"></a>  CKeyFrame::AddToStoryboardAtOffset

添加关键帧偏移量位置处的情节提要。

```
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>参数

*pStoryboard*<br/>
指向情节提要的指针。

*bDeepAdd*<br/>
指定是否要添加关键帧此关键帧依赖于以递归方式。

### <a name="return-value"></a>返回值

为 TRUE，如果关键帧已成功添加。

### <a name="remarks"></a>备注

要添加关键帧偏移量位置处的情节提要的框架调用此函数。

##  <a name="ckeyframe"></a>  CKeyFrame::CKeyFrame

构造取决于过渡的关键帧。

```
CKeyFrame(CBaseTransition* pTransition);


CKeyFrame(
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>参数

*pTransition*<br/>
指向过渡的指针。

*pKeyframe*<br/>
指向关键帧的指针。

*offset*<br/>
偏移量，以秒为单位，从由 pKeyframe 指定关键帧。

### <a name="remarks"></a>备注

指定的转换结束时，构造的关键帧将表示在 storyboard 时刻。

##  <a name="getexistingkeyframe"></a>  CKeyFrame::GetExistingKeyframe

返回指向此关键帧依赖的关键帧的指针。

```
CBaseKeyFrame* GetExistingKeyframe();
```

### <a name="return-value"></a>返回值

指向关键帧，则为 NULL，如果此关键帧不依赖于其他关键帧的有效指针。

### <a name="remarks"></a>备注

这是对依赖此关键帧的关键帧的访问器。

##  <a name="getoffset"></a>  CKeyFrame::GetOffset

返回从其他关键帧的偏移量。

```
UI_ANIMATION_SECONDS GetOffset();
```

### <a name="return-value"></a>返回值

数秒内从其他关键帧中的偏移量。

### <a name="remarks"></a>备注

应调用此方法，以确定在数秒内从其他关键帧的偏移量。

##  <a name="gettransition"></a>  CKeyFrame::GetTransition

返回一个指向此关键帧所依赖的转换。

```
CBaseTransition* GetTransition();
```

### <a name="return-value"></a>返回值

指向转换，则为 NULL，如果此关键帧不依赖于转换的有效指针。

### <a name="remarks"></a>备注

这是对转换取决于此关键帧的访问器。

##  <a name="m_offset"></a>  CKeyFrame::m_offset

指定从关键帧 m_pExistingKeyFrame 中存储此关键帧的偏移量。

```
UI_ANIMATION_SECONDS m_offset;
```

##  <a name="m_pexistingkeyframe"></a>  CKeyFrame::m_pExistingKeyFrame

存储指向现有关键帧的指针的指针。 此关键帧添加到与现有的关键帧的 m_offset 情节提要。

```
CBaseKeyFrame* m_pExistingKeyFrame;
```

##  <a name="m_ptransition"></a>  CKeyFrame::m_pTransition

存储指向过渡的关键帧开始。

```
CBaseTransition* m_pTransition;
```

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
