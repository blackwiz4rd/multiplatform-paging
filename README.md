# Multiplatform Paging

This library packages [Jetpack Paging] for Kotlin/Multiplatform.

Our multiplatform APIs use `app.cash.paging`.
This library delegates to the stock Jetpack Paging artifact on the Android platform.

Note that commonMain includes only the Paging 3 APIs from `androidx.paging`.
We don't plan to offer multiplatform APIs for Paging 2.

## API Discrepancies

Our common API is the same as `androidx.paging`, copied to `app.cash.paging`.
All types in `app.cash.paging` typealias to `androidx.paging` on all platforms.

Unfortunately, there are a few exceptions, due to limitations in the Kotlin compiler.

| `androidx.paging`                                      | `app.cash.paging`                         | Issue reference                               |
|--------------------------------------------------------|-------------------------------------------|-----------------------------------------------|
| LoadState.NotLoading                                   | LoadStateNotLoading                       | https://youtrack.jetbrains.com/issue/KT-34281 |
| LoadState.Loading                                      | LoadStateLoading                          | https://youtrack.jetbrains.com/issue/KT-34281 |
| LoadState.Error                                        | LoadStateError                            | https://youtrack.jetbrains.com/issue/KT-34281 |
| PagingConfig.Companion.MAX_SIZE_UNBOUNDED              | MAX_SIZE_UNBOUNDED                        | https://youtrack.jetbrains.com/issue/KT-18856 |
| PagingSource.LoadParams<Key>                           | PagingSourceLoadParams<Key>               | https://youtrack.jetbrains.com/issue/KT-34281 |
| PagingSource.LoadParams.Refresh<Key>                   | PagingSourceLoadParamsRefresh<Key>        | https://youtrack.jetbrains.com/issue/KT-34281 |
| PagingSource.LoadParams.Append<Key>                    | PagingSourceLoadParamsAppend<Key>         | https://youtrack.jetbrains.com/issue/KT-34281 |
| PagingSource.LoadParams.Prepend<Key>                   | PagingSourceLoadParamsPrepend<Key>        | https://youtrack.jetbrains.com/issue/KT-34281 |
| PagingSource.LoadResult.Error<Key, Value>              | PagingSourceLoadResultError<Key, Value>   | https://youtrack.jetbrains.com/issue/KT-34281 |
| PagingSource.LoadResult.Invalid<Key, Value>            | PagingSourceLoadResultInvalid<Key, Value> | https://youtrack.jetbrains.com/issue/KT-34281 |
| PagingSource.LoadResult.Page<Key, Value>               | PagingSourceLoadResultPage<Key, Value>    | https://youtrack.jetbrains.com/issue/KT-34281 |
| PagingSource.LoadResult.Page.Companion.COUNT_UNDEFINED | COUNT_UNDEFINED                           | https://youtrack.jetbrains.com/issue/KT-18856 |
| RemoteMediator.MediatorResult                          | RemoteMediatorMediatorResult              | https://youtrack.jetbrains.com/issue/KT-34281 |
| RemoteMediator.MediatorResult.Error                    | RemoteMediatorMediatorResultError         | https://youtrack.jetbrains.com/issue/KT-34281 |
| RemoteMediator.MediatorResult.Success                  | RemoteMediatorMediatorResultSuccess       | https://youtrack.jetbrains.com/issue/KT-34281 |
| RemoteMediator.InitializeAction                        | RemoteMediatorInitializeAction            | https://youtrack.jetbrains.com/issue/KT-34281 |

## Versioning

Multiplatform Paging follows the [same version numbers](https://mvnrepository.com/artifact/androidx.paging/paging-common) as Jetpack's Paging.
We will (or won't?) follow alpha/beta/rc releases of androidx/paging.
In the case of patch releases affecting just Multiplatform Paging, we will append `-patchX` (e.g., `app.cash.paging:paging-common:3.1.1-patch01`).
Catching up to the latest release of Jetpack's Paging may take some time due to potential issues making the new KMP compatible.
A tracking issue will be created and pinned each time we are lagging behind a version.

It's similar to the [versioning of KSP](https://mvnrepository.com/artifact/com.google.devtools.ksp/symbol-processing) where it's the androidx-paging version number followed by our number.

[Jetpack Paging]: https://developer.android.com/topic/libraries/architecture/paging/v3-overview

## License

    Copyright 2022 Block, Inc.

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.