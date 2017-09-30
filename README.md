# CVonMac

Set up OpenCV and TensorFlow on Mac.  Based on a tutorial [on PyImageSearch](https://www.pyimagesearch.com/2016/12/05/macos-install-opencv-3-and-python-3-5/).

# Download these scripts

    git clone git@github.com:sarah-j-smith/CVonMac.git
    
    cd CVonMac

# Install XCode

If you don't have Xcode set up yet, download it, and install the command line tools.

![Install via Mac App Store](install-xcode.png)

Type the following commands into the Mac `Terminal`:

    sudo xcodebuild -license

    sudo xcode-select --install

# Install Pre-requisites

    // [Homebrew](https://brew.sh)
    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    brew update

    // Set up paths for Brew
    cat bash_profile >> ~/.bash_profile
    source ~/.bash_profile

    // Set up Python 3
    brew install python3

    // Set up links so that python3 from Brew is used
    // The command brew linkapps is deprecated so try the following
    (cd /usr/local/bin & sudo ln -s $(find -L /usr/local/Cellar -name python3 -perm +111 -type f | head -1))

    // Check its working properly - the below will print nothing if all is OK
    [ "/usr/local/bin/python3" == $(which python3) ] || echo "Python 3 is not setup correctly"

    // Install virtualenv & virtualenvwrapper
    // These create a sandboxed Python environment
    pip install virtualenv virtualenvwrapper

    // Set up paths for virtualenv & virtualenvwrapper
    cat >> bash_profile.2 >> ~/.bash_profile
    source ~/.bash_profile

    // Create a virtualenv for python
    mkvirtualenv cv -p python3

    // From now use this command to enter the virtualenv for CV and Python3
    workon cv

    // Check its working properly - the below will print nothing if all is OK
    [ "$HOME/.virtualenvs/cv/bin/python3" == $(which python3) ] || echo "Python 3 virtualenv is not set up correctly"

    // Install build pre-requisites for OpenCV
    brew install cmake pkg-config
    brew install jpeg libpng libtiff openexr
    brew install eigen tbb


# Get OpenCV sources

    // Check [The OpenCV releases and get the latest one](http://opencv.org/releases.html)
    curl -O https://github.com/opencv/opencv/archive/3.3.0.zip
    unzip 3.3.0.zip

    // Check the matching [release for OpenCV contrib](https://github.com/opencv/opencv_contrib/releases)
    curl -O https://github.com/opencv/opencv_contrib/archive/3.3.0.zip
    unzip 3.3.0.zip
