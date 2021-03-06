---
title: CAtlFile 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlFile
- ATLFILE/ATL::CAtlFile
- ATLFILE/ATL::CAtlFile::CAtlFile
- ATLFILE/ATL::CAtlFile::Create
- ATLFILE/ATL::CAtlFile::Flush
- ATLFILE/ATL::CAtlFile::GetOverlappedResult
- ATLFILE/ATL::CAtlFile::GetPosition
- ATLFILE/ATL::CAtlFile::GetSize
- ATLFILE/ATL::CAtlFile::LockRange
- ATLFILE/ATL::CAtlFile::Read
- ATLFILE/ATL::CAtlFile::Seek
- ATLFILE/ATL::CAtlFile::SetSize
- ATLFILE/ATL::CAtlFile::UnlockRange
- ATLFILE/ATL::CAtlFile::Write
- ATLFILE/ATL::CAtlFile::m_pTM
dev_langs:
- C++
helpviewer_keywords:
- CAtlFile class
ms.assetid: 93ed160b-af2a-448c-9cbe-e5fa46c199bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ec124d1010a5870d47b9f1504655a7822505fe6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040487"
---
# <a name="catlfile-class"></a>CAtlFile 类

此类提供了 Windows 的薄包装器文件处理 API。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
class CAtlFile : public CHandle
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAtlFile::CAtlFile](#catlfile)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAtlFile::Create](#create)|调用此方法来创建或打开文件。|
|[CAtlFile::Flush](#flush)|调用此方法以清除文件缓冲区并导致所有缓冲的数据写入到文件。|
|[CAtlFile::GetOverlappedResult](#getoverlappedresult)|调用此方法以获取对该文件的重叠操作的结果。|
|[CAtlFile::GetPosition](#getposition)|调用此方法以从文件中获取当前文件指针位置。|
|[CAtlFile::GetSize](#getsize)|调用此方法以获取以字节为单位的文件的大小。|
|[CAtlFile::LockRange](#lockrange)|调用此方法以锁定以防止其他进程对其进行访问的文件中的区域。|
|[CAtlFile::Read](#read)|调用此方法以从文件的文件指针所指示的位置开始读取数据。|
|[CAtlFile::Seek](#seek)|调用此方法以将该文件的文件指针移动。|
|[CAtlFile::SetSize](#setsize)|调用此方法以设置文件的大小。|
|[CAtlFile::UnlockRange](#unlockrange)|调用此方法以解锁该文件的区域。|
|[CAtlFile::Write](#write)|调用此方法将数据写入文件指针指示的位置开始的文件。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CAtlFile::m_pTM](#m_ptm)|指向`CAtlTransactionManager`对象|

## <a name="remarks"></a>备注

当文件处理需求相对简单，但不是 Windows API 提供了更多抽象是必需的而无需包括 MFC 依赖项时，请使用此类。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CHandle](../../atl/reference/chandle-class.md)

`CAtlFile`

## <a name="requirements"></a>要求

**标头：** atlfile.h

##  <a name="catlfile"></a>  CAtlFile::CAtlFile

构造函数。

```
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```

### <a name="parameters"></a>参数

文件<br/>
文件对象中。

*hFile*<br/>
文件句柄。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="remarks"></a>备注

复制构造函数将从原始传输的文件句柄所有权`CAtlFile`对象与新构造的对象。

##  <a name="create"></a>  CAtlFile::Create

调用此方法来创建或打开文件。

```
HRESULT Create(
    LPCTSTR szFilename,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes = FILE_ATTRIBUTE_NORMAL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    HANDLE hTemplateFile = NULL) throw();
```

### <a name="parameters"></a>参数

*szFilename*<br/>
文件名。

*dwDesiredAccess*<br/>
所需的访问。 请参阅*dwDesiredAccess*中[CreateFile](/windows/desktop/api/fileapi/nf-fileapi-createfilea) Windows SDK 中。

*dwShareMode*<br/>
共享模式中。 请参阅*dwShareMode*中`CreateFile`。

*dwCreationDisposition*<br/>
创建处理设置。 请参阅*dwCreationDisposition*中`CreateFile`。

*dwFlagsAndAttributes*<br/>
标志和属性。 请参阅*dwFlagsAndAttributes*中`CreateFile`。

*lpsa*<br/>
安全属性。 请参阅*lpSecurityAttributes*中`CreateFile`。

*hTemplateFile*<br/>
模板文件中。 请参阅*hTemplateFile*中`CreateFile`。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

调用[CreateFile](/windows/desktop/api/fileapi/nf-fileapi-createfilea)若要创建或打开文件。

##  <a name="flush"></a>  CAtlFile::Flush

调用此方法以清除文件缓冲区并导致所有缓冲的数据写入到文件。

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

调用[FlushFileBuffers](/windows/desktop/api/fileapi/nf-fileapi-flushfilebuffers)将缓冲的数据刷新到文件。

##  <a name="getoverlappedresult"></a>  CAtlFile::GetOverlappedResult

调用此方法以获取对该文件的重叠操作的结果。

```
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```

### <a name="parameters"></a>参数

*给 pOverlapped*<br/>
重叠的结构。 请参阅*lpOverlapped*中[GetOverlappedResult](/windows/desktop/api/ioapiset/nf-ioapiset-getoverlappedresult) Windows SDK 中。

*dwBytesTransferred*<br/>
传送的字节数。 请参阅*lpNumberOfBytesTransferred*中`GetOverlappedResult`。

*bWait*<br/>
等待选项。 请参阅*bWait*中`GetOverlappedResult`。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

调用[GetOverlappedResult](/windows/desktop/api/ioapiset/nf-ioapiset-getoverlappedresult)来获取对该文件的重叠操作的结果。

##  <a name="getposition"></a>  CAtlFile::GetPosition

调用此方法以获取当前文件指针位置。

```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>参数

*nPos*<br/>
中字节的位置。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

调用[SetFilePointer](/windows/desktop/api/fileapi/nf-fileapi-setfilepointer)来获取当前文件指针位置。

##  <a name="getsize"></a>  CAtlFile::GetSize

调用此方法以获取以字节为单位的文件的大小。

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>参数

*nLen*<br/>
在文件中的字节数。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

调用[GetFileSize](/windows/desktop/api/fileapi/nf-fileapi-getfilesize)以获取以字节为单位的文件的大小。

##  <a name="lockrange"></a>  CAtlFile::LockRange

调用此方法以锁定以防止其他进程对其进行访问的文件中的区域。

```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>参数

*nPos*<br/>
锁开始处的文件中的位置。

*nCount*<br/>
要锁定的字节范围的长度。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

调用[锁定文件](/windows/desktop/api/fileapi/nf-fileapi-lockfile)锁定文件中的区域。 锁定文件中的字节将阻止其他进程访问这些字节。 可锁定多个区域文件，但允许使用任何重叠区域。 如果解除锁定区域，使用[CAtlFile::UnlockRange](#unlockrange)，字节范围必须完全对应以前锁定的区域。 `LockRange` 不会合并相邻区域;如果有两种锁定的区域相邻，必须单独解锁每个。

##  <a name="m_ptm"></a>  CAtlFile::m_pTM

指向 `CAtlTransactionManager` 对象的指针。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>备注

##  <a name="read"></a>  CAtlFile::Read

调用此方法以从文件的文件指针所指示的位置开始读取数据。

```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();
```

### <a name="parameters"></a>参数

*pBuffer*<br/>
指向将接收从文件中读取数据的缓冲区的指针。

*nBufSize*<br/>
缓冲区大小（以字节为单位）。

*nBytesRead*<br/>
读取的字节数。

*给 pOverlapped*<br/>
重叠的结构。 请参阅*lpOverlapped*中[ReadFile](/windows/desktop/api/fileapi/nf-fileapi-readfile) Windows SDK 中。

*pfnCompletionRoutine*<br/>
完成例程。 请参阅*lpCompletionRoutine*中[ReadFileEx](/windows/desktop/api/fileapi/nf-fileapi-readfileex) Windows SDK 中。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

前三个窗体调用[ReadFile](/windows/desktop/api/fileapi/nf-fileapi-readfile)，上次[ReadFileEx](/windows/desktop/api/fileapi/nf-fileapi-readfileex)从文件读取数据。 使用[CAtlFile::Seek](#seek)移动文件指针。

##  <a name="seek"></a>  CAtlFile::Seek

调用此方法以将该文件的文件指针移动。

```
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>参数

*nOffset*<br/>
从给定的起始点的偏移量*dwFrom*。

*dwFrom*<br/>
起始点 （FILE_BEGIN、 FILE_CURRENT 或 FILE_END）。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

调用[SetFilePointer](/windows/desktop/api/fileapi/nf-fileapi-setfilepointer)移动文件指针。

##  <a name="setsize"></a>  CAtlFile::SetSize

调用此方法以设置文件的大小。

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>参数

*nNewLen*<br/>
以字节为单位的文件的新长度。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

调用[SetFilePointer](/windows/desktop/api/fileapi/nf-fileapi-setfilepointer)并[SetEndOfFile](/windows/desktop/api/fileapi/nf-fileapi-setendoffile)设置文件的大小。 返回时，文件指针定位在文件末尾。

##  <a name="unlockrange"></a>  CAtlFile::UnlockRange

调用此方法以解锁该文件的区域。

```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>参数

*nPos*<br/>
解锁开始处的文件中的位置。

*nCount*<br/>
要将其解锁的字节范围的长度。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

调用[UnlockFile](/windows/desktop/api/fileapi/nf-fileapi-unlockfile)解锁该文件的区域。

##  <a name="write"></a>  CAtlFile::Write

调用此方法将数据写入文件指针指示的位置开始的文件。

```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();
```

### <a name="parameters"></a>参数

*pBuffer*<br/>
包含要写入到文件的数据的缓冲区。

*nBufSize*<br/>
要从缓冲区传输的字节数。

*给 pOverlapped*<br/>
重叠的结构。 请参阅*lpOverlapped*中[WriteFile](/windows/desktop/api/fileapi/nf-fileapi-writefile) Windows SDK 中。

*pfnCompletionRoutine*<br/>
完成例程。 请参阅*lpCompletionRoutine*中[writefileex 只写入](/windows/desktop/api/fileapi/nf-fileapi-writefileex)Windows SDK 中。

*pnBytesWritten*<br/>
写入的字节数。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

前三个窗体调用[WriteFile](/windows/desktop/api/fileapi/nf-fileapi-writefile)，最后一个调用[writefileex 只写入](/windows/desktop/api/fileapi/nf-fileapi-writefileex)将数据写入该文件。 使用[CAtlFile::Seek](#seek)移动文件指针。

## <a name="see-also"></a>请参阅

[字幕示例](../../visual-cpp-samples.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[CHandle 类](../../atl/reference/chandle-class.md)
