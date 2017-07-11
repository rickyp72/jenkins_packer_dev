#!groovy

node {
  branch=env.ghphTargetBranch ? env.ghphTargetBranch : env.BRANCE_NAME
  def err = null
  currentBuild.result = "SUCCESS"

  try {
    stage 'Checkout'
      checkout scm

    stage 'Validate'
      def packer_file = 'ova_creater_new.json'

      print "Running packer validate on : ${packer_file}"



    stage 'Build'
      print "building something"

    stage 'Test'
      print "Testing goes here."
      sh "ls -ltr ~/"
  }

  catch (caughtError) {
    err = caughtError
    currentBuild.result = "FAILURE"
  }

  finally {
    /* Must re-throw exception to propagate error */
    if (err) {
      throw err
    }
  }
}
