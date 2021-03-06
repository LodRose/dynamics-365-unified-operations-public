---
# required metadata

title: Deployment guidelines for cash registers for Norway
description: This topic is a deployment guide for the Retail localization for Norway.
author: AlexChern0v
manager: olegkl
ms.date: 10/23/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Norway
ms.search.industry: Retail
ms.author: v-alexec
ms.search.scope: Retail
ms.search.validFrom: 2017-10-15
ms.dyn365.ops.version: Application update 4
---
# Deployment guidelines for cash registers for Norway

[!include[banner](../includes/banner.md)]

This topic is a deployment guide that shows how to enable the Microsoft Dynamics 365 for Retail localization for Norway. The localization consists of several extensions of Retail components. For example, the extensions let you print custom fields on receipts, register additional audit events and sales and payment transactions in Point of Sale (POS), digitally sign sales transactions, and print X and Z reports in local formats. For more information about the Retail localization for Norway, see [Cash registers for Norway](./emea-nor-cash-registers.md).

This sample is part of the Retail software development kit (SDK). For information about how to install and use the Retail SDK, see the [Retail SDK documentation](../dev-itpro/retail-sdk/retail-sdk-overview.md).

This sample consists of extensions for the Commerce runtime (CRT), Retail Server, and POS. To run this sample, you must modify and build the CRT, Retail Server, and POS projects. We recommend that you use an unmodified Retail SDK to make the changes that are described in this topic. We also recommend that you use a source control system, such as Microsoft Visual Studio Online (VSO), where no files have been changed yet.

> [!NOTE] 
> Some steps in the procedures in this topic differ if you have Microsoft Dynamics 365 for Finance and Operations, Enterprise edition with application update 4 instead of a later version.

## Development environment

Follow these steps to set up a development environment, so that you can test and extend the sample.

### The CRT extension components

The CRT extension components are included in the CRT samples. To complete the following procedures, open the CRT solution, **CommerceRuntimeSamples.sln**, under **RetailSdk\\SampleExtensions\\CommerceRuntime**.

#### ReceiptsNorway component

1. Find the **Runtime.Extensions.ReceiptsNorway** project, and build it.
2. In the **Extensions.ReceiptsNorway\\bin\Debug** folder, find the **Contoso.Commerce.Runtime.ReceiptsNorway.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the Internet Information Services (IIS) Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extensions configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extensions configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsNorway" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### RegisterAuditEvent sample component

1. Find the **Runtime.Extensions.RegisterAuditEventSample** project, and build it.
2. In the **Extensions.RegisterAuditEventSample\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.RegisterAuditEventSample.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extensions configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extensions configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.RegisterAuditEventSample" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SalesPaymentTransExt component

1. Find the **Runtime.Extensions.SalesPaymentTransExt** project, and build it.
2. In the **Extensions.SalesPaymentTransExt\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SalesPaymentTransExt.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extensions configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extensions configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SalesTransactionSignature sample component

1. Find the **Runtime.Extensions.SalesTransactionSignatureSample** project.
2. Modify the **App.config** file by specifying the thumbprint, store location, and store name for the certificate that should be used to sign sales transactions. Then build the project.
3. In the **Extensions.SalesTransactionSignatureSample\\bin\\Debug** folder, find the following files:

    - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll** assembly file
    - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config** configuration file

3. Copy the files to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extensions configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extensions configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SalesTransactionSignatureSample.Messages component (Application update 5)

> [!NOTE]
> This section applies only to Microsoft Dynamics 365 for Finance and Operations, Enterprise edition with application update 5 and later.

1. Find the **Runtime.Extensions.SalesTransactionSignatureSample.Messages** project.
2. In the **Extensions.SalesTransactionSignatureSample.Messages\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.Messages.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extensions configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extensions configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample.Messages" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### XZReportsNorway component

1. Find the **Runtime.Extensions.XZReportsNorway** project, and build it.
2. In the **Extensions.XZReportsNorway\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.XZReportsNorway.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extensions configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extensions configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsNorway" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

### The Retail Server extension components

#### SalesTransactionSignature Retail Server sample component

1. In the **RetailSDK\\SampleExtensions\\RetailServer\\RetailServer.Extensions.SalesTransactionSignatureSample** folder, find the **RetailServer.Extensions.SalesTransactionSignatureSample** project, and build it.
2. In the **RetailServer\\Extensions.SalesTransactionSignatureSample\\bin\\Debug** folder, find the **Contoso.RetailServer.SalesTransactionSignatureSample.dll** assembly file.
3. Copy the assembly file to the **\\bin** folder under the IIS Retail Server site location.
4. Find the configuration file for Retail Server. The file is named **web.config**, and it's in the root folder under the IIS Retail Server site location.
5. Register the Retail Server extensions in the **extensionComposition** section of the configuration file.

    ``` xml
    <add source="assembly" value="Contoso.RetailServer.SalesTransactionSignatureSample" />
    ```

6. Register the dependencies of the Retail Server extensions.

    > [!NOTE]
    > This step differs for Application update 4 and for later versions. Follow the steps in one of the following sections, depending on the version that you're using. 

    - For Application update 4

        1. In the **CommerceRuntime\\Extensions.SalesTransactionSignatureSample\\bin\\Debug** folder, find the following files:

            - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll** assembly file
            - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config** configuration file

        2. Copy the files to the **\\bin** folder under the IIS Retail Server site location.
        3. Register the CRT change in the extensions configuration file for CRT. This file is named **commerceruntime.ext.config**, and it's in the **bin** folder under the IIS Retail Server site location.

            ``` xml
            <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample" />
            ```

            > [!WARNING]
            > - Do **not** edit the commerceruntime.config file. This file isn't intended for any customizations. 
            > - This step resembles the step for including the SalesTransactionSignature CRT extension component, but it uses a different destination folder: bin instead of bin\\ext. You must use the bin folder to help guarantee that the Retail Server extension is successfully loaded.

    - For Application update 5 and later

        1. In the **CommerceRuntime\\Extensions.SalesTransactionSignatureSample.Messages\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.Messages.dll** assembly file.
        2. Copy the file to the **\\bin** folder under the IIS Retail Server site location.
        3. Register the CRT change in the extensions configuration file for CRT. This file is named **commerceruntime.ext.config**, and it's in the **bin** folder under the IIS Retail Server site location.

            ``` xml
            <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample.Messages" />
            ```

            > [!WARNING]
            > - Do **not** edit the commerceruntime.config file. This file isn't intended for any customizations. 
            > - This step resembles the step for including the SalesTransactionSignature.Messages CRT extension component, but it uses a different destination folder: bin instead of bin\\ext. You must use the bin folder to help guarantee that the Retail Server extension is successfully loaded.

### The Modern POS extension components

#### Implement the proxy code for offline mode 

This part is equivalent to the Retail Server controller, but it extends the local CRT that is used when the client isn't connected.

1. In the **customization.settings** file, change the **@(RetailServerLibraryPathForProxyGeneration)** section so that it uses the new Retail Server assembly for proxy generation.
2. Implement the following interface methods in the **StoreOperationsManager** class. For the first iteration, add the following code:

    - For Application update 4, add the following code.

        ``` csharp
        public Task<bool> SalesTransactionSignatureServiceIsReady()
        {
            throw new NotImplementedException();
        }
        public Task<FiscalTransaction> GetLastFiscalTransaction(string storeNumber, string terminalId)
        {
            throw new NotImplementedException();
        }
        ```

    - For Application update 5 and later, add the following code.

        ``` csharp
        public Task<bool> SalesTransactionSignatureServiceIsReady(string correlationId)
        {
            throw new NotImplementedException();
        }
        public Task<FiscalTransaction> GetLastFiscalTransaction(string storeNumber, string terminalId)
        {
            throw new NotImplementedException();
        }
        ```

3. To regenerate the proxy code, build the **Proxies** folder from the command line (use the **msbuild /t:Rebuild** command)

4. Resolve the **Proxies.RetailProxy** project dependencies:

    - For Application update 4

        Open the **RetailSDK\\Proxies\\RetailProxy\\Proxies.RetailProxy.csproj**, add the **RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.SalesTransactionSignatureSample\\CommerceRuntime.Extensions.SalesTransactionSignatureSample** project to the solution, and add a project reference to the **RetailProxy** project to reference **SalesTransactionSignatureSample**.

    - For Application update 5 and later

        Open **RetailSDK\\Proxies\\RetailProxy\\Proxies.RetailProxy.csproj**, add the **RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.SalesTransactionSignatureSample.Messages\\CommerceRuntime.Extensions.SalesTransactionSignatureSample.Messages** project to the solution, and add a project reference to the **RetailProxy** project to reference **SalesTransactionSignatureSample.Messages**.

5. Adjust the interface methods in the **StoreOperationsManager** class:

    - For Application update 4, adjust the following code.

        ``` csharp
        public Task<bool> SalesTransactionSignatureServiceIsReady()
        {
            return Task.Run(() => CommerceRuntimeManager.Runtime.Execute<SalesTransactionSignatureServiceIsReadyResponse>(new SalesTransactionSignatureServiceIsReadyRequest(), null).IsReady);
        }
        public Task<FiscalTransaction> GetLastFiscalTransaction(string storeNumber, string terminalId)
        {
            return Task.Run(() => CommerceRuntimeManager.Runtime.Execute<GetLastFiscalTransactionResponse>(new GetLastFiscalTransactionRequest(), null).FiscalTransaction);
        }
        ```

    - For Application update 5 and later, adjust the following code.

        ``` csharp
        public Task<bool> SalesTransactionSignatureServiceIsReady(string correlationId)
        {
            return Task.Run(() => CommerceRuntimeManager.Runtime.Execute<SalesTransactionSignatureServiceIsReadyResponse>(new SalesTransactionSignatureServiceIsReadyRequest(), null).IsReady);
        }
        public Task<FiscalTransaction> GetLastFiscalTransaction(string storeNumber, string terminalId)
        {
            return Task.Run(() => CommerceRuntimeManager.Runtime.Execute<GetLastFiscalTransactionResponse>(new GetLastFiscalTransactionRequest(), null).FiscalTransaction);
        }
        ```

6. Update the **dllhost.exe.config** file so that the client broker loads the new RetailProxy assembly.

    ``` xml
    <add key="RetailProxyAssemblyName" value="Contoso.Commerce.RetailProxy" />
    <add key="AdaptorCallerFullTypeName" value="Contoso.Commerce.RetailProxy.Adapters.AdaptorCaller" />
    ```

#### Modern POS extension components

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**, and make sure that it can be compiled without errors. Additionally, make sure that you can run Modern POS from Microsoft Visual Studio by using the **Run** command.

    > [!NOTE]
    > Modern POS must not be customized. You must enable User Account Control (UAC), and you must uninstall previously installed instances of Modern POS as required.

2. Include existing **AuditEventExtensionSample** and **SalesTransactionSignatureSample** source code folders in the **Pos.Extensions** project.
3. Enable the extensions to be compiled in **tsconfig.json** by removing the **AuditEventExtensionSample** and **SalesTransactionSignatureSample** folders from the exclude list.
4. Enable the extensions to be loaded in **extensions.json** by adding the following lines in the appropriate place.

    ``` json
    {
        "baseUrl": "AuditEventExtensionSample"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    }
    ```

    > [!NOTE]
    > For more information, and for samples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file in the **Pos.Extensions** project.

5. Rebuild the solution.
6. Run Modern POS in the debugger, and test the functionality.

### The Cloud POS extension components

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**, and make sure that it can be compiled without errors.
2. Include existing **AuditEventExtensionSample** and **SalesTransactionSignatureSample** source code folders in the **Pos.Extensions** project.
3. Enable the extensions to be compiled in **tsconfig.json** by removing the **AuditEventExtensionSample** and **SalesTransactionSignatureSample** folders from the exclude list.
4. Enable the extensions to be loaded in **extensions.json** by adding the following lines in the appropriate place.

    ``` json
    {
        "baseUrl": "AuditEventExtensionSample"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    }
    ```

    > [!NOTE]
    > For more information, and for samples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file in the **Pos.Extensions** project.

5. Rebuild the solution.
6. Run the solution by using the **Run** command and following the steps in the Retail SDK handbook.
7. Test the functionality.

### Set up required parameters in Retail headquarters

For more information, see [Cash registers for Norway](./emea-nor-cash-registers.md).

## Production environment

Follow these steps to create deployable packages that contain Retail components, and to apply those packages in a production environment.

1. Make the following changes in the package configuration files under the **RetailSdk\\Assets** folder:

    1. In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files, add the following lines to the **composition** section:

        - For Application update 4, add the following lines.

            ``` xml
            <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsNorway" />
            <add source="assembly" value="Contoso.Commerce.Runtime.RegisterAuditEventSample" />
            <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
            <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample" />
            <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsNorway" />
            ```

        - For Application update 5 and later, add the following lines.

            ``` xml
            <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsNorway" />
            <add source="assembly" value="Contoso.Commerce.Runtime.RegisterAuditEventSample" />
            <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
            <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample" />
            <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample.Messages" />
            <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsNorway" />
            ```

    2. In the **dllhost.exe.config** configuration file, add the following lines to the **appSettings** subsection of the **configuration** section.

        ``` xml
        <add key="RetailProxyAssemblyName" value="Contoso.Commerce.RetailProxy"/>
        <add key="AdaptorCallerFullTypeName" value ="Contoso.Commerce.RetailProxy.Adapters.AdaptorCaller"/>
        ```

2. Make the following changes in the **Customization.settings** package customization configuration file:

    1. Add the following lines to the **&lt;ItemGroup Condition="'@(RetailServerLibraryPathForProxyGeneration)' == ''"&gt;** section.

        ``` xml
        <RetailServerLibraryPathForProxyGeneration Include="$(SdkReferencesPath)\Contoso.RetailServer.SalesTransactionSignatureSample.dll"/>
        ```

    2. Add the following lines to the **ItemGroup** section to include the CRT extensions in the deployable packages:

        - For Application update 4, add the following lines.

            ``` xml
            <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.ReceiptsNorway.dll" />
            <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.RegisterAuditEventSample.dll" />
            <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExt.dll" />
            <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll" />
            <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config" />
            <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.XZReportsNorway.dll" />
            ```

        - For Application update 5 and later, add the following lines.

            ``` xml
            <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.ReceiptsNorway.dll" />
            <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.RegisterAuditEventSample.dll" />
            <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExt.dll" />
            <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll" />
            <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config" />
            <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureSample.Messages.dll" />
            <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.XZReportsNorway.dll" />
            ```

    3. Add following lines to the **ItemGroup** section to include the Retail Server extension in the deployable packages:

        - For Application update 4, add the following lines.

            ``` xml
            <ISV_RetailServer_CustomizableFile Include="$(SdkReferencesPath)\Contoso.RetailServer.SalesTransactionSignatureSample.dll" />
            <ISV_RetailServer_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll" />
            <ISV_RetailServer_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config" />
            ```

        - For Application update 5 and later, add the following lines.

            ``` xml
            <ISV_RetailServer_CustomizableFile Include="$(SdkReferencesPath)\Contoso.RetailServer.SalesTransactionSignatureSample.dll" />
            <ISV_RetailServer_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureSample.Messages.dll" />
            ```

3. Run **msbuild** for the whole Retail SDK to create deployable packages.
4. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Retail SDK packaging](../dev-itpro/retail-sdk/retail-sdk-packaging.md).

### Enable the digital signature in offline mode for Modern POS

To enable the digital signature in offline mode for Modern POS, you must follow these steps after you activate Modern POS on a new device.

1. Sign in to POS.
2. On the **Database connection status** page, make sure that the offline database is fully synchronized. When the value of the **Pending downloads** field is **0** (zero), the database is fully synchronized.
3. Sign out of POS.
4. Wait a while for the offline database to be fully synchronized.
5. Sign in to POS.
6. On the **Database connection status** page, make sure that the offline database is fully synchronized. When the value of the **Pending transactions in offline database** field is **0** (zero), the database is fully synchronized.
7. Restart Modern POS.
