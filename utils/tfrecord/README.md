The code base was developed and is maintained by Marc Fischer (marc.fischer@iss.uni-stuttgart.de)<br/>
-- Many thanks for that --

## Usage
The example folder shows how to parse into tfrecord and load it with tensorflow.

1. ex_conv_set.py: it parse all the data in the folder into tfrecord and save them into another directory

                    convert_dir.dir2tf -- parse_gen.parse_data_gen(find the required file path)
                    -- read_image.read_mat_image(load image) -- convert_tf.im2tfrecord(parse into tfrecord and save)


2. ex_pipeline_simple.py: it saves a image into a tmp dir and reload it to see if save successfully.

                    An import point here is to try save it in the simple data format, for example, don't save as
                    tf.float64 if it could be save as tf.int16. Otherwise it will reduce the speed largely.

3. ex_pipeline_folder.py: ex_pipeline_folder2.py: samply load the patch sample per image with tensorflow session.

                    tfrecord are loaded with convert_tf.parse_function, and patch is got  with tf.slice.

4. ex_pipeline_folder2.py: for each image, spliited it with tf.random_crop, which make good use of the images.

                    refers to: https://stackoverflow.com/questions/48777889/tf-data-api-how-to-efficiently-sample-small-patches-from-images

5. ex_pipeline_folder3.py: for each image, create the index list to specify which patch shall be cropped.
                    
                    The train flolder shows how to use input pipeline with a keras model.

1. multiclass_3D_CNN.py: a simple CNN architectureblock. All the basic part should be imported from tf.keras instead of keras

2. create_dataset: create the train image/label generator

3. train.py: a simple model how to convert the model into estimator and run.
