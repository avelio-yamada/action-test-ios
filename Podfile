# Uncomment the next line to define a global platform for your project
platform :ios, '12.0'

target 'github-action' do
  # Comment the next line if you don't want to use dynamic frameworks
  use_frameworks!

  # Pods for github-action
  pod 'Firebase/Analytics', '~> 8.5.0'
  pod 'Firebase/DynamicLinks', '~> 8.5.0'
  pod 'MercariQRScanner', '~> 1.8.0'
end

target 'github-actionTests' do
  # Comment the next line if you don't want to use dynamic frameworks
  use_frameworks!

  # Pods for github-action
  pod 'Firebase/Analytics', '~> 8.5.0'
  pod 'Firebase/DynamicLinks', '~> 8.5.0'
  pod 'MercariQRScanner', '~> 1.8.0'
end

post_install do |installer|
    installer.pods_project.build_configurations.each do |config|
        if config.name == "Develop"
            config.build_settings['ONLY_ACTIVE_ARCH'] = 'YES'
            config.build_settings['DEBUG_INFORMATION_FORMAT'] = 'dwarf'
            config.build_settings['GCC_OPTIMIZATION_LEVEL'] = '0'
            config.build_settings['SWIFT_COMPILATION_MODE'] = 'singlefile'
            config.build_settings['SWIFT_OPTIMIZATION_LEVEL'] = '-Onone'
            config.build_settings['MTL_ENABLE_DEBUG_INFO'] = 'INCLUDE_SOURCE'
            config.build_settings['ENABLE_NS_ASSERTIONS'] = 'YES'
            config.build_settings['ENABLE_TESTABILITY'] = 'YES'

            preprocessor_definitions = config.build_settings['GCC_PREPROCESSOR_DEFINITIONS'] || ['$(inherited)']
            preprocessor_definitions = [preprocessor_definitions] unless preprocessor_definitions.instance_of?(Array)
            preprocessor_definitions.push('DEBUG=1').uniq!
            config.build_settings['GCC_PREPROCESSOR_DEFINITIONS'] = preprocessor_definitions
        end
    end

    installer.pods_project.targets.each do |target|
        target.build_configurations.each do |config|
            config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '12.0'
        end
    end
end