#!groovy

node {

  def err = null
  currentBuild.result = "SUCCESS"

  try {
    stage 'Checkout'
      checkout scm

    stage 'Validate'
      def packer_file = 'packer_aws_inspec_rhel_jenk.json'
      print "Running packer validate on : ${packer_file}"
      sh "packer -v ; packer validate ${packer_file} \| tee build.log"

    stage 'Build'
      sh "packer build ${packer_file}"

    stage 'Test'
      print "Testing goes here."
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
