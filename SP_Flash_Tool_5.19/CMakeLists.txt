cmake_minimum_required(VERSION 3.5)

project(SP_Flash VERSION 0.1 LANGUAGES CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Widgets Core Gui PrintSupport Network XmlPatterns)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Widgets Core Gui PrintSupport Network XmlPatterns)

set(PROJECT_SOURCES
        main.cpp
        FlashToolApp.cpp
        Arg/AutoFormatArg.cpp         
        Arg/BromFormatArg.cpp    
        Arg/NANDForamtArg.cpp
        # Arg/AutoFormatArgFactory.cpp 
        Arg/BromMemtestArg.cpp   
        Arg/NORFormatArg.cpp
        Arg/BootRomArg.cpp            
        Arg/BromOTPArg.cpp       
        Arg/SDMMCAutoFormatArg.cpp
        Arg/BromAdapterArg.cpp        
        Arg/BromReadbackArg.cpp  
        Arg/UFSFormatArg.cpp
        Arg/BromChksumArg.cpp
        Arg/EMMCFormatArg.cpp   
        Arg/WriteMemoryArg.cpp
        Arg/BromDownloadArg.cpp
        Arg/GeneralArg.cpp
        Cmd/BromAdapterCommand.cpp      
        Cmd/ICommand.cpp
        Cmd/CertDLCommand.cpp            
        Cmd/MacroCommand.cpp
        Cmd/CheckRPMBCommand.cpp         
        Cmd/MemoryTestCommand.cpp
        Cmd/ComboFormatCommand.cpp       
        Cmd/OTPCommand.cpp
        Cmd/DADownloadAll.cpp            
        Cmd/ReadbackCommand.cpp
        Cmd/DeviceTestCommand.cpp        
        Cmd/ReadbackWithoutScatterCommand.cpp
        Cmd/DLOnlyCommand.cpp            
        Cmd/RSCCommand.cpp
        Cmd/DLPlugFmtAllCommand.cpp      
        Cmd/SCIDownloadCommand.cpp
        Cmd/DLWithoutScatterCommand.cpp  
        Cmd/SCIRBCommand.cpp
        Cmd/DRAMRepairCommand.cpp        
        Cmd/SCIRestoreCommand.cpp
        Cmd/EfuseCommand.cpp             
        Cmd/SecDLCommand.cpp
        Cmd/FirmwareUpgradeCommand.cpp   
        Cmd/SetBootModeCommand.cpp
        Cmd/FormatCommand.cpp            
        Cmd/WatchDogCommand.cpp
        Cmd/FWCommand.cpp                
        Cmd/WriteMemoryCommand.cpp
        Cmd/GeneralCommand.cpp
        Conn/Connection.cpp  
        Conn/ConnImpl.cpp  
        Conn/ConnMedia.cpp  
        Conn/USBSetting.cpp
        ConsoleMode/CommandLineArguments.cpp     
        ConsoleMode/Config.cpp            
        ConsoleMode/SchemaValidator.cpp
        ConsoleMode/CommandSetting.cpp           
        ConsoleMode/ConsoleModeEntry.cpp
        ConsoleMode/CommandSettingValidator.cpp  
        ConsoleMode/GeneralSetting.cpp
        Err/AppException.cpp   
        Err/BromException.cpp  
        Err/UserStopException.cpp
        Err/BaseException.cpp  
        Err/ErrorLookup.cpp
        Flow/concreterom.cpp  
        Flow/dlproxyimpl.cpp  
        Flow/restoreworker.cpp
        Flow/defaultrom.cpp   
        Flow/ErrString.cpp    
        Flow/romfactory.cpp
        Flow/dlproxy.cpp      
        Flow/NvramVerify.cpp  
        Flow/storhelper.cpp
        Host/Linux/CriticalSectionSentry.cpp  
        Host/Linux/DeviceConn.cpp  
        Host/Linux/DeviceScan.cpp  
        Host/Linux/RuntimeMemory.cpp
        JSONParser/json.cpp
        Logger/Log.cpp  
        Logger/Logger.cpp
        Public/AppCore.cpp  
        Public/RomInfoFactory.cpp
        Resource/CoreHandle.cpp  
        Resource/ResourceManager.cpp
        Resource/Handle/AuthHandle.cpp  
        Resource/Handle/DAHandle.cpp  
        Resource/Handle/DLHandle.cpp  
        Resource/Handle/RBHandle.cpp  
        Resource/Handle/ScretHandle.cpp
        Rules/ChksumRule.cpp  
        Rules/PlatformRule.cpp  
        Rules/ReadbackRule.cpp  
        Rules/StorageRule.cpp
        Setting/BromAdapterSetting.cpp       
        Setting/FWSetting.cpp
        Setting/CertDLSetting.cpp            
        Setting/LogInfoSetting.cpp
        Setting/CheckRPMBSetting.cpp         
        Setting/MemoryTestSetting.cpp
        Setting/ChksumSetting.cpp            
        Setting/OTPSetting.cpp
        Setting/ComboFormatSetting.cpp       
        Setting/PlatformSetting.cpp
        Setting/ConnBromUARTSetting.cpp      
        Setting/ReadbackSettingAssist.cpp
        Setting/ConnBromUSBSetting.cpp       
        Setting/ReadbackSetting.cpp
        Setting/ConnSetting.cpp              
        Setting/ReadbackWithoutScatterSetting.cpp
        Setting/DADownloadAllSetting.cpp     
        Setting/RSCSetting.cpp
        Setting/DeviceTestSetting.cpp        
        Setting/SCIDownloadSetting.cpp
        Setting/DLOnlySetting.cpp            
        Setting/SCIRBSetting.cpp
        Setting/DLPlugFmtAllSetting.cpp      
        Setting/SCIRestoreSetting.cpp
        Setting/DLWithoutScatterSetting.cpp  
        Setting/SecDLSetting.cpp
        Setting/DRAMRepairSetting.cpp        
        Setting/SetBootModeSetting.cpp
        Setting/EfuseSetting.cpp             
        Setting/WatchDogSetting.cpp
        Setting/FirmwareUpgradeSetting.cpp   
        Setting/WriteMemorySetting.cpp
        Setting/FormatSetting.cpp
        TimeStamp/TempPlcCtrl.cpp
        Utility/CloneInfo.cpp   
        Utility/USBCOMFinderWrapper.cpp
        Utility/LogFilesClean.cpp   
        Utility/constString.cpp 
        Utility/Utils.cpp
        Utility/sendreport.cpp 
        Utility/FileUtils.cpp   
        Utility/version.cpp
        Utility/SizeCalcHelper.cpp  
        Utility/IniItem.cpp
        XMLParser/tinystr.cpp 
        XMLParser/tinystr.h 
        XMLParser/tinyxml.cpp 
        XMLParser/tinyxml.h 
        XMLParser/tinyxmlerror.cpp 
        XMLParser/tinyxmlparser.cpp 
        XMLParser/XMLDocument.cpp 
        XMLParser/XMLDocument.h 
        XMLParser/XMLDocumentImpl.cpp 
        XMLParser/XMLDocumentImpl.h 
        XMLParser/XMLNode.cpp 
        XMLParser/XMLNode.h 
        XMLParser/XMLNodeImpl.cpp 
        XMLParser/XMLNodeImpl.h 
        XMLParser/XMLSerializable.h
        UI/forms/MainWindow.ui 
        # UI/src/MainWindow.cpp 
        # UI/src/MainWindow.h 
        UI/forms/TabWidget/BromAdapterWidget.ui 
        UI/forms/TabWidget/CloneDownloadWidget.ui 
        UI/forms/TabWidget/DeviceTestWidget.ui 
        UI/forms/TabWidget/DownloadWidget.ui 
        UI/forms/TabWidget/FormatWidget.ui 
        UI/forms/TabWidget/fw.ui 
        UI/forms/TabWidget/MemoryTestWidget.ui 
        UI/forms/TabWidget/ParameterWidget.ui 
        UI/forms/TabWidget/ReadBackWidget.ui 
        UI/forms/TabWidget/SCIDownloadWidget.ui 
        UI/forms/TabWidget/WelcomeWidget.ui 
        UI/forms/TabWidget/WriteMemoryWidget.ui
        UI/forms/AboutDialog.ui 
        # UI/src/AboutDialog.cpp 
        # UI/src/AboutDialog.h 
        UI/forms/CheckUpdateDialog.ui 
        UI/forms/ChipInfoWidget.ui 
        UI/forms/EMMCWidget.ui 
        UI/forms/EncryDialog.ui 
        UI/forms/NandWidget.ui 
        UI/forms/NorFlashWidget.ui 
        UI/forms/OkDialog.ui 
        UI/forms/OptionDialog.ui 
        UI/forms/OTPReadDialog.ui 
        UI/forms/OTPWritedialog.ui 
        UI/forms/ProcessingDialog.ui 
        UI/forms/ReadBackAddressDialog.ui 
        UI/forms/SDMMCWidget.ui 
        UI/forms/SecuritySettingDialog.ui 
        UI/forms/UfsWidget.ui 
        UI/forms/UpdateDialog.ui   
        UI/src/Assistant.cpp 
        UI/src/Assistant.h 
        UI/src/AsyncResourceLoader.cpp 
        UI/src/AsyncResourceLoader.h 
        UI/src/AsyncUARTComPortInfo.cpp 
        UI/src/AsyncUARTComPortInfo.h 
        UI/src/AsyncUpdater.cpp 
        UI/src/AsyncUpdater.h 
        UI/src/BackgroundWorker.cpp 
        UI/src/BackgroundWorker.h 
        # UI/src/BromAdapterWidget.cpp 
        # UI/src/BromAdapterWidget.h 
        UI/src/CheckHeader.cpp 
        UI/src/CheckHeader.h 
        # UI/src/CheckUpdateDialog.cpp 
        # UI/src/CheckUpdateDialog.h 
        # UI/src/ChipInfoWidget.cpp 
        # UI/src/ChipInfoWidget.h 
        # UI/src/CloneDownloadWidget.cpp 
        # UI/src/CloneDownloadWidget.h 
        UI/src/connob.cpp 
        UI/src/connob.h 
        # UI/src/DeviceTestWidget.cpp 
        # UI/src/DeviceTestWidget.h 
        UI/src/DLDelegate.cpp 
        UI/src/DLDelegate.h 
        # UI/src/DownloadWidget.cpp 
        # UI/src/DownloadWidget.h 
        # UI/src/EMMCWidget.cpp 
        # UI/src/EMMCWidget.h 
        # UI/src/EncryDialog.cpp 
        # UI/src/EncryDialog.h 
        # UI/src/FormatWidget.cpp 
        # UI/src/FormatWidget.h 
        # UI/src/fw.cpp 
        # UI/src/fw.h 
        UI/src/ICallback.h 
        UI/src/MainController.cpp 
        UI/src/MainController.h 
        # UI/src/MainWindowCallback.cpp 
        # UI/src/MainWindowCallback.h 
        # UI/src/MemoryTestWidget.cpp 
        # UI/src/MemoryTestWidget.h 
        # UI/src/NandWidget.h 
        # UI/src/NandWidgetd.cpp 
        # UI/src/NorFlashWidget.cpp 
        # UI/src/NorFlashWidget.h 
        # UI/src/OkDialog.cpp 
        # UI/src/OkDialog.h 
        # UI/src/OptionDialog.cpp 
        # UI/src/OptionDialog.h 
        # UI/src/OTPReadDialog.cpp 
        # UI/src/OTPReadDialog.h 
        # UI/src/OTPWriteDialog.cpp 
        # UI/src/OTPWriteDialog.h 
        # UI/src/ParameterWidget.cpp 
        # UI/src/ParameterWidget.h 
        UI/src/PlatformObj.cpp 
        UI/src/PlatformObj.h 
        UI/src/ProcessingAnimation.cpp 
        UI/src/ProcessingAnimation.h 
        # UI/src/ProcessingDialog.cpp 
        # UI/src/ProcessingDialog.h 
        # UI/src/ReadBackAddressDialog.cpp 
        # UI/src/ReadBackAddressDialog.h 
        # UI/src/ReadBackWidget.cpp 
        # UI/src/ReadBackWidget.h 
        # UI/src/ScatterObserver.cpp 
        # UI/src/ScatterObserver.h 
        # UI/src/SCIDownloadWidget.cpp 
        # UI/src/SCIDownloadWidget.h 
        # UI/src/SDMMCWidget.cpp 
        # UI/src/SDMMCWidget.h 
        # UI/src/TabWidgetBase.cpp 
        # UI/src/TabWidgetBase.h 
        # UI/src/UfsWidget.cpp 
        # UI/src/UfsWidget.h 
        # UI/src/UpdateDialog.cpp 
        # UI/src/UpdateDialog.h 
        # UI/src/WelcomeWidget.cpp 
        # UI/src/WelcomeWidget.h 
        # UI/src/WriteMemoryWidget.cpp 
        # UI/src/WriteMemoryWidget.h   
        UI/flashtool.rc 
        UI/html.qrc 
        UI/icon.qrc 
        UI/translations.qrc
        BootRom/brom.h 
        BootRom/com_enum.h 
        BootRom/common_struct.h 
        BootRom/DOWNLOAD.H 
        BootRom/external_memory_config.h 
        BootRom/flashtool_api.h 
        BootRom/flashtool_handle.h 
        BootRom/flashtool.h 
        BootRom/flashtoolex_api.h 
        BootRom/flashtoolex_struct.h 
        BootRom/host.h 
        BootRom/internal_api.h 
        BootRom/mtk_mcu.h 
        BootRom/mtk_resource.h 
        BootRom/mtk_status.h 
        BootRom/SLA_Challenge.h
        BootRom/type_define.h  
)

if(${QT_VERSION_MAJOR} GREATER_EQUAL 6)
    qt_add_executable(${PROJECT_NAME}
        MANUAL_FINALIZATION
        ${PROJECT_SOURCES}
    )
# Define target properties for Android with Qt 6 as:
#    set_property(TARGET pokus APPEND PROPERTY QT_ANDROID_PACKAGE_SOURCE_DIR
#                 ${CMAKE_CURRENT_SOURCE_DIR}/android)
# For more information, see https://doc.qt.io/qt-6/qt-add-executable.html#target-creation
else()
    if(ANDROID)
        add_library(${PROJECT_NAME} SHARED
            ${PROJECT_SOURCES}
        )
# Define properties for Android with Qt 5 after find_package() calls as:
#    set(ANDROID_PACKAGE_SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/android")
    else()
        add_executable(${PROJECT_NAME}
            ${PROJECT_SOURCES}
           # pokus.h
        )
    endif()
endif()

target_link_libraries(${PROJECT_NAME} PRIVATE Qt${QT_VERSION_MAJOR}::Widgets Qt${QT_VERSION_MAJOR}::Gui Qt${QT_VERSION_MAJOR}::Core Qt${QT_VERSION_MAJOR}::Network Qt${QT_VERSION_MAJOR}::XmlPatterns)

# Qt for iOS sets MACOSX_BUNDLE_GUI_IDENTIFIER automatically since Qt 6.1.
# If you are developing for iOS or macOS you should consider setting an
# explicit, fixed bundle identifier manually though.
if(${QT_VERSION} VERSION_LESS 6.1.0)
  set(BUNDLE_ID_OPTION MACOSX_BUNDLE_GUI_IDENTIFIER com.example.pokus)
endif()
set_target_properties(${PROJECT_NAME} PROPERTIES
    ${BUNDLE_ID_OPTION}
    MACOSX_BUNDLE_BUNDLE_VERSION ${PROJECT_VERSION}
    MACOSX_BUNDLE_SHORT_VERSION_STRING ${PROJECT_VERSION_MAJOR}.${PROJECT_VERSION_MINOR}
    MACOSX_BUNDLE TRUE
    WIN32_EXECUTABLE TRUE
)

include(GNUInstallDirs)
install(TARGETS ${PROJECT_NAME}
    BUNDLE DESTINATION .
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)

if(QT_VERSION_MAJOR EQUAL 6)
    qt_finalize_executable(pokus)
endif()
