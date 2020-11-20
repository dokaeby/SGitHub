#Uncomment the next line to define a global platform for your project
platform :ios, '13.0'

use_frameworks!
inhibit_all_warnings!

  # RX
  pod 'RxSwift', '~> 5.0'
  pod 'RxCocoa', '~> 5.0'
  pod 'RxDataSources', '~> 4.0'
  pod 'RxSwiftExt', '~> 5.0'  # https://github.com/RxSwiftCommunity/RxSwiftExt
  pod 'NSObject+Rx', '~> 5.0'  # https://github.com/RxSwiftCommunity/NSObject-Rx
  pod 'RxViewController', '~> 1.0'  # https://github.com/devxoul/RxViewController
  pod 'RxGesture', '~> 3.0'  # https://github.com/RxSwiftCommunity/RxGesture
  pod 'RxOptional', '~> 4.0'  # https://github.com/RxSwiftCommunity/RxOptional
  pod 'RxTheme', '~> 4.0'  # https://github.com/RxSwiftCommunity/RxTheme

  # FireBase
  pod 'Firebase'
  pod 'Firebase/Analytics'
  pod 'Firebase/Crashlytics'

  # Util
  pod 'SwifterSwift', '~> 5.0'  # https://github.com/SwifterSwift/SwifterSwift
  pod 'Toast-Swift', '~> 5.0'  # https://github.com/scalessec/Toast-Swift

  # Image
  pod 'Kingfisher', '~> 5.0'

  # UI
  pod 'SnapKit', '~> 4.0.0'
  pod 'SkeletonView'

  # Indicator
  pod 'NVActivityIndicatorView'

#  pod 'Hero'

  # Tools
  pod 'R.swift', '~> 5.0'  # https://github.com/mac-cain13/R.swift
  pod 'SwiftLint', '0.40.0'  # https://github.com/realm/SwiftLint
  
  # Network
  pod 'Alamofire'
  pod 'Moya/RxSwift'  # https://github.com/Moya/Moya

  # Graph QL
  pod 'Apollo', '0.31.0'  # https://github.com/apollographql/apollo-ios

  # Date
  pod 'DateToolsSwift', '~> 5.0'  # https://github.com/MatthewYork/DateTools
  pod 'SwiftDate', '~> 6.0'  # https://github.com/malcommac/SwiftDate


target 'SGitHub' do
  # Comment the next line if you're not using Swift and don't want to use dynamic frameworks
end

target 'SGitHubTests' do
  # Pods for SGitHub testing
  pod 'Quick', '~> 3.0'  # https://github.com/Quick/Quick
  pod 'Nimble', '~> 8.0'  # https://github.com/Quick/Nimble
  pod 'RxAtomic', :modular_headers => true
  pod 'RxBlocking'  # https://github.com/ReactiveX/RxSwift
end

target 'SGitHubUITests' do
  # Pods for SGitHub testing
  pod 'Quick', '~> 3.0'  # https://github.com/Quick/Quick
  pod 'Nimble', '~> 8.0'  # https://github.com/Quick/Nimble
  pod 'RxAtomic', :modular_headers => true
  pod 'RxBlocking'  # https://github.com/ReactiveX/RxSwift
end

post_install do |installer|
    # Cocoapods optimization, always clean project after pod updating
    Dir.glob(installer.sandbox.target_support_files_root + "Pods-*/*.sh").each do |script|
        flag_name = File.basename(script, ".sh") + "-Installation-Flag"
        folder = "${TARGET_BUILD_DIR}/${UNLOCALIZED_RESOURCES_FOLDER_PATH}"
        file = File.join(folder, flag_name)
        content = File.read(script)
        content.gsub!(/set -e/, "set -e\nKG_FILE=\"#{file}\"\nif [ -f \"$KG_FILE\" ]; then exit 0; fi\nmkdir -p \"#{folder}\"\ntouch \"$KG_FILE\"")
        File.write(script, content)
    end
    
    # Enable tracing resources
    installer.pods_project.targets.each do |target|
      if target.name == 'RxSwift'
        target.build_configurations.each do |config|
          if config.name == 'Debug'
            config.build_settings['OTHER_SWIFT_FLAGS'] ||= ['-D', 'TRACE_RESOURCES']
            config.build_settings['ALWAYS_EMBED_SWIFT_STANDARD_LIBRARIES'] = 'Yes'
          end
        end
      end
    end
end


